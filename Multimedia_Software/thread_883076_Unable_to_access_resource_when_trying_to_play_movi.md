---
title: "Unable to access resource when trying to play movie DVD"
date: 2008-08-07
forum: Multimedia Software
---

### Post by Julian David Pitt on 2008-08-07
I have all the medibuntu packages installed including libdvdcss2, libdvdnav4 and libdvdread but I still cannot read from encrypted DVD's. I get the following when I run totem at a terminal
```
julian@Hardy:~$ totem
** (totem:8509): DEBUG: Init of Python module
** (totem:8509): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:8509): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:8509): DEBUG: Creating Python plugin instance
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000cc4)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002c4a18)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x003433d2)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x003b3df4)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000cc4)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002c4a18)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x003433d2)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x003b3df4)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000cc4)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002c4a18)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x003433d2)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x003b3df4)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000cc4)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002c4a18)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x003433d2)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x003b3df4)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000cc4)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002c4a18)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x003433d2)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x003b3df4)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000cc4)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002c4a18)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x003433d2)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x003b3df4)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000cc4)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002c4a18)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x003433d2)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x003b3df4)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000cc4)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002c4a18)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x003433d2)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x003b3df4)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000cc4)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002c4a18)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x003433d2)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x003b3df4)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000cc4)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002c4a18)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x003433d2)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x003b3df4)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000cc4)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002c4a18)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x003433d2)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x003b3df4)!!
** Message: Error: Could not read from resource.
dvdreadsrc.c(919): gst_dvd_read_src_create (): /play/source

** (totem:8509): DEBUG: Finalizing Python plugin instance
```

**I am using hardy 8.04.1 fully updated and am desperate to get DVD playback working, your help is greatly appreciated thanks.**

---

### Post by rainwalker on 2008-08-07
Just as a test, have you tried playing the DVD with any other players? VLC and Mplayer are (in my opinion) two of the best.

---

### Post by Julian David Pitt on 2008-08-08
Hi Rainwalker
I have tried it in VLC, Mplayer and Caffeine all with the same result but it works fine on my home DVD player. From the error messages I am getting I am taking it that the player software cannot see past the encryption, is that correct?

---

### Post by rainwalker on 2008-08-09
That's what it looks like to me...I'm not an expert on it , though.
I've always done what [this thread]("http://ubuntuforums.org/showthread.php?t=766683") says, and it's worked for me since Dapper

---

