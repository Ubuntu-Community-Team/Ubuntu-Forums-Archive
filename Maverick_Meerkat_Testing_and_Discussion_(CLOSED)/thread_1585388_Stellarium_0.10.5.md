---
title: "Stellarium 0.10.5"
date: 2010-09-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by PaulW2U on 2010-09-30
I recently downloaded version 0.10.5 from the repository. The last batch of updates on 29th? September stopped stellarium from starting. I have uninstalled and reinstalled.

If I start the application from a terminal the following output is seen:

```
paul@DELL:~$ stellarium
Using default graphics system specified at build time: raster
 -------------------------------------------------------
[ This is Stellarium 0.10.5 - [http://www.stellarium.org](http://www.stellarium.org) ]
[ Copyright (C) 2000-2010 Fabien Chereau et al ]
 -------------------------------------------------------
Writing log file to: "/home/paul/.stellarium/log.txt"
File search paths:
  0 . "/home/paul/.stellarium"
  1 . "/usr/share/stellarium"
Attempting to use an existing older config file.
Config file is: "/home/paul/.stellarium/config.ini"
Qt GL paint engine is: "OpenGL"
drmRadeonCmdBuffer: -22. Kernel failed to parse or rejected command stream. See dmesg for more info.
```

A quick look at the dmesg output suggests a memory allocation problem. Stellarium works perfectly under Ubuntu 10.04 by the way.

It's very disappointing to have to report this just two weeks before the final release and I'm now having to revert to Lucid due to this. :(

[https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/652201](https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/652201)

---

### Post by cariboo on 2010-09-30
You may want to look at something else that is causing the problem, as Stellarium works well here. 

System:
[list]
[*] Custom built system
[*] AMD X2 3800+ CPU
[*] 2Gb ram
[*] Nvidia 9400GT Video Card running 256.53 driver
[*] Up-to-date Maverick 64bit kernel 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux
[/list]

---

### Post by ronacc on 2010-09-30
looks like the problem is the ATI driver , Stellarium runs fine here on AMD64 and Nvidia-current

---

### Post by 23dornot23d on 2010-09-30
Works great here .... thanks for bringing it up ..... superb fast too ....

Nvidia Graphics 256.53 driver .... GeForce 9300 GS
Laptop ..... 7730 zg - dual core processor 32 bit
3 Gig of ram.

Hope you find a solution .... do 3D programs like Blender and K3dsurf work ok ?

---

### Post by cariboo on 2010-09-30
Just another update, I just installed it on a system using the nouveau drivers with 3D enabled, and it works well on that system too. The framerate isn't as high, but it's an older system with an:

[list]
[*] AMD 3400+ single core 64-bit cpu
[*] 1Gb ram
[*] 8400GS Nvidia graphics card
[*] Up-to-date Maverick 64-bit
[/list]

---

### Post by PaulW2U on 2010-10-02
> **ronacc said:**
> looks like the problem is the ATI driver , Stellarium runs fine here on AMD64 and Nvidia-current
I changed the video card today. I now have an ATI Radeon HD4350 installed. 

Stellarium now starts but no text is displayed in any part of the program and the setup screens also fail to appear. If I install the fglrx driver then stellarium again fails to start but this time with a segmentation fault. May be an update to either stellarium or the ATI driver will be released in due course. :confused:

Still runs fine on my 10.04 set-up though. :)

---

### Post by Peter-E on 2010-10-04
[QUOTE=PaulW2U;9915726]I changed the video card today. I now have an ATI Radeon HD4350 installed. 

Lucid  worked fine with 0.10.4, provided that you use the
LC_NUMERIC=C stellarium as startup shellscript.

In  Maverick no joy at all, with or without it. I will have to dig deep again.
On my ATI Radeon I have a 

Stellarium ../../radeon/radeon_cs_gem_write_reloc: Check test 'boi>space accounted' faillure...
Aborted
test@test~$:(

---

### Post by PaulW2U on 2010-10-04
This bug - [https://bugs.launchpad.net/stellarium/+bug/481669](https://bugs.launchpad.net/stellarium/+bug/481669) was first recorded nearly a year ago so I don't think my problem is specifically Maverick related.

But I can definitely say that a recent update stopped my Maverick installation from working. :(

---

### Post by Elfy on 2010-10-08
Just in case someone else has the issue.

On a clean install here it didn't/doesn't work with the nvidia driver. I reverted to the nouveau (with the experimental 3d package) and it's fine.

---

### Post by Seren on 2010-10-08
I have got something specific here with a radeon mobility 9600 / R300 chip:

```

:~$ stellarium 
Using default graphics system specified at build time:  raster 
 ------------------------------------------------------- 
[ This is Stellarium 0.10.5 - [http://www.stellarium.org](http://www.stellarium.org) ] 
[ Copyright (C) 2000-2010 Fabien Chereau et al          ] 
 ------------------------------------------------------- 
Writing log file to: "/home/seren/.stellarium/log.txt" 
File search paths: 
  0 .  "/home/seren/.stellarium" 
  1 .  "/usr/share/stellarium" 
Attempting to use an existing older config file. 
Config file is:  "/home/seren/.stellarium/config.ini" 

stellarium(5220)/ KSharedDataCache::Private::mapSharedMemory: Opening cache "/var/tmp/kdecache-seren/icon-cache.kcache" page size is 4096
stellarium(5220)/ KSharedDataCache::Private::mapSharedMemory: Attached to cache, determining if it must be initialized
stellarium(5220)/ KSharedDataCache::Private::mapSharedMemory: Cache fully initialized -- attached to memory mapping
stellarium(5220)/ KSharedDataCache::Private::mapSharedMemory: 3948544 bytes available out of 10485760
Qt GL paint engine is:  "OpenGL" 
drmRadeonCmdBuffer: -22. Kernel failed to parse or rejected command stream. See dmesg for more info.

```

and dmesg output :

```

[ 2437.365562] [drm:r100_cs_track_check] *ERROR* [drm] Buffer too small for color buffer 0 (need 393216 have 16384) !
[ 2437.365579] [drm:r100_cs_track_check] *ERROR* [drm] color buffer 0 (128 4 0 768)
[ 2437.365587] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 2464.784227] [drm:r100_cs_track_check] *ERROR* [drm] Buffer too small for color buffer 0 (need 393216 have 16384) !
[ 2464.784239] [drm:r100_cs_track_check] *ERROR* [drm] color buffer 0 (128 4 0 768)
[ 2464.784244] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 2494.740408] [drm:r100_cs_track_check] *ERROR* [drm] Buffer too small for color buffer 0 (need 393216 have 16384) !
[ 2494.740426] [drm:r100_cs_track_check] *ERROR* [drm] color buffer 0 (128 4 0 768)
[ 2494.740435] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !

```

For some reason the command checker from the driver is rejecting specific command used at stellarium launch.

---

### Post by plun on 2010-10-08
> **forestpiskie said:**
> 
On a clean install here it didn't/doesn't work with the nvidia driver. I reverted to the nouveau (with the experimental 3d package) and it's fine.

It works excellent with the real nvidia driver....!!


```
plun@plun-laptop:~$ stellarium
Using default graphics system specified at build time:  raster 
User config directory does not exist:  "/home/plun/.stellarium" 
Creating directory  "/home/plun/.stellarium" 
 ------------------------------------------------------- 
[ This is Stellarium 0.10.5 - http://www.stellarium.org ] 
[ Copyright (C) 2000-2010 Fabien Chereau et al          ] 
 ------------------------------------------------------- 
Writing log file to: "/home/plun/.stellarium/log.txt" 
File search paths: 
  0 .  "/home/plun/.stellarium" 
  1 .  "/usr/share/stellarium" 
Config file  "/home/plun/.stellarium/config.ini"  does not exist. Copying the default file. 
Config file is:  "/home/plun/.stellarium/config.ini" 
Qt GL paint engine is:  "OpenGL2" 
Cache directory is:  "/home/plun/.cache/stellarium/stellarium" 
Sky language is  "en_US" 
Application language is  "en_US" 
Loading Solar System data ... 
Loaded 38 / 38 planet orbits 
Could not find the starsConfig.json file: will copy the default one. 
Creating directory  "/home/plun/.stellarium/stars/default" 
Creates file  "/home/plun/.stellarium/stars/default/starsConfig.json" 
Loading star data ... 
"Loading "/usr/share/stellarium/stars/default/stars_0_0v0_1.cat": 0_0v0_1; 5013" 
"Loading "/usr/share/stellarium/stars/default/stars_1_0v0_1.cat": 1_0v0_1; 21999" 
"Loading "/usr/share/stellarium/stars/default/stars_2_0v0_1.cat": 2_0v0_1; 151416" 
"Loading "/usr/share/stellarium/stars/default/stars_3_1v0_0.cat": 3_1v0_0; 434064" 
Finished loading star catalogue data, max_geodesic_level:  3 
navigation/preset_sky_time is a double - treating as jday: 2.45151e+06 
Loaded 10051 NGC records 
Loading NGC name data ... 
Loaded 222 / 222 NGC name records successfully 
Loaded 88 / 88 constellation records successfully for culture "western" 
Loaded 85 / 85 constellation art records successfully for culture "western" 
Loaded 89 / 89 constellation names 
Loading constellation boundary data ...  
Loaded 782 constellation boundary segments 
Loading star names from "/usr/share/stellarium/skycultures/western/star_names.fab" 
Loaded 230 / 230 common star names 
Loading star names from "/usr/share/stellarium/stars/default/name.fab" 
Loaded 3215 / 4359 scientific star names 
Creating GUI ... 

```

OPs challenge is with the Radeon driver !

---

