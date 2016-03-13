собирать bcc32.exe
образец параметров CMake - CMakeCache.txt

для компиляции заменить после генерации CMake во всех сгенерированных Makefile и build.make "..\\\r" на "..\r"

для линковки .dll в параметры компилятора -lGHtds=0x10000000 //http://codeverge.com/embarcadero.cppbuilder.ide/ilink32-fatal-error-not-enough-mem/1988542
например прям в build.make так:

C:\PROGRA~2\EMBARC~1\Studio\16.0\bin\bcc32.exe  -tR -tD @&&|
-e..\bin\OgreMain_d.dll -tM -lS:1048576 -lSc:4098 -lH:1048576 -lHc:8192 -lGHtds=0x10000000 -v C:\Develop\ogre181\dep-build\ogredeps\lib\debug\freetype_d.lib C:\Develop\ogre181\dep-build\ogredeps\lib\debug\FreeImage_d.lib import32.lib  $(OgreMain_OBJECTS) $(OgreMain_EXTERNAL_OBJECTS)
|
	implib -c -w ..\lib\OgreMain_d.lib ..\bin\OgreMain_d.dll
	cd ..
	