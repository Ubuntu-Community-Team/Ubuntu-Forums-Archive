---
title: "Installing LMMS through Cmake"
date: 2009-02-12
forum: Multimedia Software
---

### Post by Eeeff on 2009-02-12
I'm not entirely sure if this is the correct category to be posting this error, but I'm having troubles installing LMMS because of certain Compiler issues, here's the output when I try and run Cmake in terminal:

[PHP]-- The C compiler identification is GNU
-- The CXX compiler identification is unknown
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: CMAKE_CXX_COMPILER-NOTFOUND
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
CMake Error: Internal CMake error, TryCompile configure of cmake failed
-- Check for working CXX compiler: CMAKE_CXX_COMPILER-NOTFOUND -- broken
CMake Error at /usr/share/cmake-2.6/Modules/CMakeTestCXXCompiler.cmake:25 (MESSAGE):
  The C++ compiler "CMAKE_CXX_COMPILER-NOTFOUND" is not able to compile a
  simple test program.

  It fails with the following output:

   

  

  CMake will not be able to correctly generate this project.
Call Stack (most recent call first):
  CMakeLists.txt:3 (PROJECT)


CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Configuring done
[/PHP]

---

### Post by Eeeff on 2009-02-12
bump

---

### Post by mc4man on 2009-02-12
Here's a thread from a few weeks ago, look thru (plus option for a .deb for 8.10

[http://ubuntuforums.org/showthread.php?t=1046909](http://ubuntuforums.org/showthread.php?t=1046909)

Edit: I forgot that I made a .deb for 8.04 and uploaded it to mediafire. If all else fails and your using Hardy it's still there, just follow the pre install instructions and the post install (creating a proper menu item in post # 7

---

