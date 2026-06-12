---
title: "no sound"
date: 2009-03-05
forum: Multimedia Software
---

### Post by cortezthekiller on 2009-03-05
Hey guys,

First, let me say that I have gone through all the steps in [Comprehensive Sound Problems]("http://ubuntuforums.org/showthread.php?t=205449") here on the forums.

I have an old-ish (2000-2001) gateway laptop with an intel chipset sound:

```
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and the hardware is listed as:

```
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

To answer a couple questions before you ask them:
-Yes, I have checked all the audio levels and the power switch on my stereo.
-It appears that the ALSA Driver exists (I believe its snd-ac'97-codec)
-I tried the sudo-modprobe-
-This is a *fresh* install of Ubuntu, I haven't has a chance to change any settings and mess something up.
-I have tried the ALSA driver compilation and got the following errors:
```
cortez@cortez-laptop:~$ sudo apt-get install build-essential linux-headers-$(uname -r) module-assist asla-source

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-11-generic is already the newest version.
E: Couldn't find package module-assist

```
```
cortez@cortez-laptop:~$ sudo dpkg-reconfigure asla-source
Package `asla-source' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: asla-source is not installed

```

I am stuck here.  Any ideas?

---

### Post by wolfen69 on 2009-03-05
> **cortezthekiller said:**
> 
E: Couldn't find package **module-assist**


it's module-assistant, not module-assist.

after you get module-assistant installed, you can then do:
```
sudo m-a a-i alsa
``` 
to see if the latest alsa will help.

btw, m-a a-i means module assistant auto install.

---

### Post by cortezthekiller on 2009-03-05
well I did that and it went though the unpacking and installing (the blue window) until about 50% than got another error:

 Build of the package alsa-source failed! 

in the log it says:

 ```
&#9474; /usr/src/modules/alsa-driver/acore/info.c: In function                     &#9618;
 &#9474; &#8216;resize_info_buffer&#8217;:                                                      &#9618;
 &#9474; /usr/src/modules/alsa-driver/acore/info.c:90: error: implicit              &#9618;
 &#9474; declaration of function &#8216;PAGE_ALIGN&#8217;                                       &#9618;
 &#9474; make[5]: *** [/usr/src/modules/alsa-driver/acore/info.o] Error 1           &#9618;
 &#9474; make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2                  &#9618;
 &#9474; make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2                &#9618;
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'      &#9618;
 &#9474; make[2]: *** [compile] Error 2                                             &#9618;
 &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9618;
 &#9474; make[1]: *** [build-stamp] Error 2                                         &#9618;
 &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9646;
 &#9474; make: *** [kdist_image] Error 2  
```

man, this is driving me crazy!

---

### Post by cortezthekiller on 2009-03-05
hey, sorry to have to bump this, but I am pulling may hair out over this.

any other suggestions?

---

