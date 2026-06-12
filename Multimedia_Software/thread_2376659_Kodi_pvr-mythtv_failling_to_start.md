---
title: "Kodi pvr-mythtv failling to start"
date: 2017-11-04
forum: Multimedia Software
---

### Post by BarnOwl on 2017-11-04
pvr-mythtv sometimes fails to start and it takes kodi down with it.  It'll start several days in a row then it will fail and it takes several reboots to get it to start again.  I'm running it from a shell script that waits until the mythtv backend is available before starting Kodi.  

The version information from the crash log is:

```
############## Kodi CRASH LOG ###############

################ SYSTEM INFO ################
 Date: Sat Nov  4 14:05:09 EDT 2017
 Kodi Options: 
 Arch: x86_64
 Kernel: Linux 4.13.0-16-generic #19-Ubuntu SMP Wed Oct 11 18:35:14 UTC 2017
 Release: Ubuntu 17.10 (Artful Aardvark)
############## END SYSTEM INFO ##############

############### STACK TRACE #################
gdb not installed, can't get stack trace.
############# END STACK TRACE ###############

################# LOG FILE ##################

<U+FEFF>14:04:57.822 T:140305240861120  NOTICE: special://profile/ is mapped to:
 special://masterprofile/
14:04:57.822 T:140305240861120  NOTICE: ----------------------------------------
-------------------------------
14:04:57.822 T:140305240861120  NOTICE: Starting Kodi (17.3 Git:20170525-nogitfo
und). Platform: Linux x86 64-bit
14:04:57.822 T:140305240861120  NOTICE: Using Release Kodi x64 build
14:04:57.822 T:140305240861120  NOTICE: Kodi compiled Nov  4 2012 by GCC 6.2.0 for Linux x86 64-bit version 4.8.17 (264209)
14:04:57.822 T:140305240861120  NOTICE: Running on Ubuntu 17.10, kernel: Linux x86 64-bit version 4.13.0-16-generic
14:04:57.843 T:140305240861120  NOTICE: FFmpeg version/source: ffmpeg-3.1-kodi
14:04:57.843 T:140305240861120  NOTICE: Host CPU: Intel(R) Atom(TM) CPU D525 @ 1.80GHz, 4 cores available

```

The actual error is:

```
14:05:08.606 T:140302337693440   ERROR: AddOnLog: MythTV PVR Client: (CPPMyth)BindObject: failed (-22) field "EndOffset" type 5: -10
14:05:08.952 T:140302337693440  NOTICE: AddOnLog: MythTV PVR Client: Launcher stopped
14:05:08.989 T:140303520950016  NOTICE: PVRManager - stopping
14:05:09.028 T:140302648059648   ERROR: AddOnLog: MythTV PVR Client: (CPPMyth)BindObject: failed (-22) field "EndOffset" type 5: -10

```

The entire log can be viewed ar: [https://pastebin.com/CzWasPSw]("https://pastebin.com/CzWasPSw")

Any ideas would be appreciated.

---

