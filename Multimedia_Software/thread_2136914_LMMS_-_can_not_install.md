---
title: "LMMS - can not install"
date: 2013-04-19
forum: Multimedia Software
---

### Post by DerpyHoovesPL on 2013-04-19
I have some trouble with installing LMMS by Cmake.

This is what Cmake returns

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
PROCESSOR: x86_64
Machine: x86_64-linux-gnu
-- Target host is 64 bit
-- Looking for include files LMMS_HAVE_STDINT_H
-- Looking for include files LMMS_HAVE_STDINT_H - found
-- Looking for include files LMMS_HAVE_STDLIB_H
-- Looking for include files LMMS_HAVE_STDLIB_H - found
-- Looking for include files LMMS_HAVE_PTHREAD_H
-- Looking for include files LMMS_HAVE_PTHREAD_H - found
-- Looking for include files LMMS_HAVE_SEMAPHORE_H
-- Looking for include files LMMS_HAVE_SEMAPHORE_H - found
-- Looking for include files LMMS_HAVE_UNISTD_H
-- Looking for include files LMMS_HAVE_UNISTD_H - found
-- Looking for include files LMMS_HAVE_SYS_TYPES_H
-- Looking for include files LMMS_HAVE_SYS_TYPES_H - found
-- Looking for include files LMMS_HAVE_SYS_IPC_H
-- Looking for include files LMMS_HAVE_SYS_IPC_H - found
-- Looking for include files LMMS_HAVE_SYS_SHM_H
-- Looking for include files LMMS_HAVE_SYS_SHM_H - found
-- Looking for include files LMMS_HAVE_SYS_TIME_H
-- Looking for include files LMMS_HAVE_SYS_TIME_H - found
-- Looking for include files LMMS_HAVE_SYS_WAIT_H
-- Looking for include files LMMS_HAVE_SYS_WAIT_H - found
-- Looking for include files LMMS_HAVE_SYS_SELECT_H
-- Looking for include files LMMS_HAVE_SYS_SELECT_H - found
-- Looking for include files LMMS_HAVE_STDARG_H
-- Looking for include files LMMS_HAVE_STDARG_H - found
-- Looking for include files LMMS_HAVE_SIGNAL_H
-- Looking for include files LMMS_HAVE_SIGNAL_H - found
-- Looking for include files LMMS_HAVE_SCHED_H
-- Looking for include files LMMS_HAVE_SCHED_H - found
-- Looking for include files LMMS_HAVE_SYS_SOUNDCARD_H
-- Looking for include files LMMS_HAVE_SYS_SOUNDCARD_H - found
-- Looking for include files LMMS_HAVE_SOUNDCARD_H
-- Looking for include files LMMS_HAVE_SOUNDCARD_H - not found.
-- Looking for include files LMMS_HAVE_FCNTL_H
-- Looking for include files LMMS_HAVE_FCNTL_H - found
-- Looking for include files LMMS_HAVE_SYS_IOCTL_H
-- Looking for include files LMMS_HAVE_SYS_IOCTL_H - found
-- Looking for include files LMMS_HAVE_CTYPE_H
-- Looking for include files LMMS_HAVE_CTYPE_H - found
-- Looking for include files LMMS_HAVE_STRING_H
-- Looking for include files LMMS_HAVE_STRING_H - found
-- Looking for include files LMMS_HAVE_PROCESS_H
-- Looking for include files LMMS_HAVE_PROCESS_H - not found.
-- Looking for include files LMMS_HAVE_LOCALE_H
-- Looking for include files LMMS_HAVE_LOCALE_H - found
CMake Error at /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:91 (MESSAGE):
  Could NOT find Qt4 (missing: QT_QMAKE_EXECUTABLE QT_MOC_EXECUTABLE
  QT_RCC_EXECUTABLE QT_UIC_EXECUTABLE QT_INCLUDE_DIR QT_LIBRARY_DIR
  QT_QTCORE_LIBRARY) (Required is at least version
  "4.3.0;COMPONENTS;QtCore;QtGui;QtXml")
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:252 (_FPHSA_FAILURE_MESSAGE)
  /usr/share/cmake-2.8/Modules/FindQt4.cmake:1171 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
  CMakeLists.txt:90 (FIND_PACKAGE)




-- Configuring incomplete, errors occurred!



Can anybody help me to solve it?

---

