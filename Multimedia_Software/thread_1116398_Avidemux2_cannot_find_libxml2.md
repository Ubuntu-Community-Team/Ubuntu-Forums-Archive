---
title: "Avidemux2 cannot find libxml2"
date: 2009-04-04
forum: Multimedia Software
---

### Post by burntresistor on 2009-04-04
I'm trying to install this and the error im getting is that it cant find libxml2 i looked in packages and it says its already been installed. What can I do to fix this cause I heard it was a alternative to virtual dub
I assume this is the problem because when i enter in the command make next it says no target specified 


:~/avidemux_2.4_branch$ cmake .
#####################################
Configure Started
#####################################
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
EXTRA Cflags:
EXTRA CXXflags:
-- <Checking for Subversion>
-- <***********************>
-- Getting svn version from /home/pandora/avidemux_2.4_branch
-- Current revision is 4721
-- <Checking for PKG-CONFIG>
-- <***********************>
-- OK /usr/bin/pkg-config
-- <Checking for LibXML2>
-- <*********************>
CMake Error at CMakeLists.txt:74 (MESSAGE):
  Could not find Libxml2

---

