---
title: "Soundcard detection Dell OptiPlex GX1"
date: 2008-11-20
forum: Multimedia Software
---

### Post by ronux on 2008-11-20
Hello All - 

Installed Xubuntu via Alternate on an old Dell OptiPlex GX1.

Soundcard is not detected.
Found this **Comprehensive Sound Problem Solutions Guide**
[http://ubuntuforums.org/showthread.php?t=205449&highlight=intel+audio+driver]("http://ubuntuforums.org/showthread.php?t=205449&highlight=intel+audio+driver")

Great resource.
Followed steps all the way but holding the **Getting the ALSA drivers from a *fresh* kernel**
for the moment.

See code 
```
alsamixer
```
is not detected.
Why??
This would be a step to finalize the process.
I found the chipset module CS4236 and CS4236lib using
```
sudo modprobe snd-
```
but it seems that the soundcard is not being loaded.

Thanks for suggestions and feedback.

R.

Note
**PC specs**
[http://support.dell.com/support/edocs/systems/ban_gx1/specs.htm]("http://support.dell.com/support/edocs/systems/ban_gx1/specs.htm")

---

### Post by FakeOutdoorsman on 2008-11-21
I have this same machine, but it's just a headless development server and database backup running Debian Etch.  Here's helpful post:
[1st Time Install - No Audio {dell optiplex gx1}]("http://ubuntuforums.org/showthread.php?t=905814")

The Ubuntu Documentation also mentioned the GX1: [How to Setup Sound Cards]("https://help.ubuntu.com/community/HowToSetupSoundCards").  It's an older article, but might work.

---

### Post by ronux on 2008-11-21
Thanks FakeOutdoorsman for this reply.
I already came across one of the links that you posted and I will give it a try.
I am wondering why the "alsamixer" line does not work at all.
Maybe because the soundcard is undetected? 
The chipset module is in place but cannot load the soundcard. :confused:


Regards.

R.

---

