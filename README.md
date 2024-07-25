# Disable Autoreverse for Snowrunner
This is a fork of FluffierKittens SnowRunner-UI-Changes (https://github.com/FluffierKittens/SnowRunner-UI-Changes). All I did was comment out the ATTACH/DETACH lines for everything except the AutoReverse blocking. So now it _should_ only stop AutoReverse behaviour without changing things like winching, etc. That means that the ONLY way to reverse is to shift the transmission into reverse, which is just the way I like it! Patches to SnowRunner WILL break this, so hopefully FK keeps updating their code for each new version!

## Features

### AUTO REVERSE
Disables AUTO REVERSE. The only way to reverse is now with the dedicated R gear. That's it!

### ############################################################################ ###
### This mod is only compatible with SnowRunner.exe version 1.510203.SNOW_DLC_13 ###
### ############################################################################ ###

## Installation
1. build the source (see below)
2. find  *SRUIC.dll* and *SRUICInjector.exe* files in the build subfolders
3. Place *SRUIC.dll* in the game folder where SnowRunner.exe is located. 
4. Place *SRUICInjector.exe* anywhere that you find convenient. The game folder is just fine.

## Usage
1. Start SnowRunner
2. Run *SRUICInjector.exe* and make sure you get a message indicating success. 
3. Start a new game or open an existing save, and have fun!

## Dependencies
This project requires Microsoft Detours, which is also available on Github (https://github.com/microsoft/Detours.git). In fact, it requires you to build the 64-bit version of Detours. Here's how I did that, after I cloned it locally:
1. installed more dependencies, detours requires ".Net desktop build tools" along with the MSVC stuff that this code already needs
2. open the "x64 Native Tools Command Prompt" and navigated to the detours dir.
3. set it to do x64:
SET DETOURS_TARGET_PROCESSOR=X64
call "\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\VC\Auxiliary\Build\vcvars64.bat"
(note: I got that from the following link, I'm not 100% sure it's mandatory. https://github.com/microsoft/Detours/issues/5)
4. then just run "nmake". That should build they 64 bit versions, you can tell because the folders they end up in are called something.X64 instead of something.X86.
5. find detours.h in there and put it in DLL/include/detours.h
6. find detours.lib and put it in DLL/lib/detours.lib (lib folder may not exist, make it!)

## Building
I'm not a software developer, and really just muddled my way through building this with lots of help from copilot. It uses cmake, so I made a "build" subdirectory and then ran:
cd build
cmake ..
cmake --build . --config Release

and ended up with the two files I needed in some subfolders of the build directory.