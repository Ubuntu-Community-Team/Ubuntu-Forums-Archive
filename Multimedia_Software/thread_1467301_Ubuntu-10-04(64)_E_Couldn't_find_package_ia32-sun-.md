---
title: "Ubuntu-10-04(64): E: Couldn't find package ia32-sun-java6-bin"
date: 2010-04-30
forum: Multimedia Software
---

### Post by AkiraBergman on 2010-04-30
I get an error while running the recommended commands in the Multimedia & Video thread;

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
"Comprehensive Multimedia & Video Howto"

The first group of commands run OK. The second group gives the following printout;

> nuri@nuri:~$ sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs ia32-sun-java6-bin icedtea6-plugin libmp3lame0 non-free-codecs openjdk-6-jre unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-ffmpeg is already the newest version.
E: Couldn't find package ia32-sun-java6-bin
nuri@nuri:~$

---

### Post by howefield on 2010-04-30
Try activating the partner repository in your Software Sources (System > Administration > Software Sources > Other Software tab)

Reload the package list and try again.

---

### Post by AkiraBergman on 2010-04-30
It worked, thank you.

---

### Post by howefield on 2010-04-30
> **AkiraBergman said:**
> It worked, thank you.


Just as I expected.

You're welcome.

---

### Post by Stringher on 2010-08-25
Thanks Man, Works for me !

---

