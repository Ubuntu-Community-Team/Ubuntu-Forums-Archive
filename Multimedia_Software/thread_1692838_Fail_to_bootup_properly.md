---
title: "Fail to bootup properly"
date: 2011-02-22
forum: Multimedia Software
---

### Post by kcxzero on 2011-02-22
Sony Vaio pcg-6w1L
Ubuntu 10.10
Nvidia 8400M GS

I'm a new ubuntu user and have been trying to get my system to bootup properly after installing the NVIDIA accelerated graphics driver (version current). I've searched and attempted for the past few days and found a few posts and articles describing similar problems as mine but the solutions don't seem to work.

This post describes the same problem I am having on bootup [http://ubuntuforums.org/showthread.php?t=1592889](http://ubuntuforums.org/showthread.php?t=1592889) but the solution does not work for me.

On bootup instead of going into the GUI splash screen it goes to a full screen terminal same, as the link above. After 5 minutes a command prompt appears requesting me to log in. I wait, eventually it goes into the GUI log in screen and everything works as normal from there.

I run glxgears without the driver installed and get around 500, with it installed 3000.

If anyone knows of a solution to this, please let me know. Thanks, much appreciated.

---

### Post by kcxzero on 2011-02-22
I'm not sure if this has anything to do with it, but more information can't hurt. When trying to locate the xorg.conf file, it isn't located at /etc/X11/xorg.conf. Instead it is here /usr/share/doc/xserver-xorg-video-nouveau/examples/xorg.conf

Also, the xorg.conf file contains Driver "nouveau" in the driver section. I've tried changing that once before to Nvidia. But if I remember correctly, doing that resulted in me having to reinstall ubuntu cause it wouldn't boot at all. But I'm feeling that file has something to do with my problem. I may have just done it incorrectly. Thanks again.

UPDATE: [http://ubuntuforums.org/showthread.php?t=1592889](http://ubuntuforums.org/showthread.php?t=1592889)

So Apparently those instruction were correct the entire time. I must have done something wrong during my first attempt (new user). I can Gladly say my computer is successfully booting up with the Nvidia driver installed. The issues I initially stated at the beginning of this post has been resolved. Additionally, unlike the link, "changing the PowerMizer settings to 'Prefer Maximum Performance'  (System > Administration > NVIDIA X Server Settings >  Powermizer (under GeForce 8400M GS)" did eliminate the stuttering for me. Also, I'm able to run the visual effects on Extra and experience some entertaining visual effects, if you're into that.

---

