---
title: "Comprehensive Multimedia &amp; Video Howto - NOT WORKING WITH MEERKAT"
date: 2010-10-16
forum: Multimedia Software
---

### Post by arepaking on 2010-10-16
Hello Everyone,
The well known Comprehensive Multimedia & Video Howto is not working with Ubuntu 10.10

I followed the INSTALLATION -> UBUNTU FAMILY 8.10 AND HIGHER USERS ONLY but I only get the following errors:


```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs ia32-sun-java6-bin icedtea6-plugin libmp3lame0 non-free-codecs openjdk-6-jre unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'libflashsupport' can't be removed
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ia32-sun-java6-bin
E: Unable to locate package non-free-codecs
```

There is no doubt that this list ought to be updated.

---

### Post by Nightstrike2009 on 2010-10-16
Have you tryed typing this into terminal:
> 
sudo apt-get update

Then trying to install them again?

---

### Post by alfitch0619 on 2010-10-16
If you have not done so, install the Medibuntu repositories as described in the Guide.  Also, go to System>Administration>Software Source and the Other Software tab and make sure Canonical Partners and Independent are checked.

---

### Post by arepaking on 2010-10-16
Thanks guys for your help.

The problem was that Canonical Partners and Independent were not checked. That was the default setting though. I wonder why. Anyways, after checking those boxes it started to download the needed packages.


Kind Regards,
AK

---

