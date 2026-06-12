---
title: "FGLRX will not work on ATI"
date: 2006-11-23
forum: Multimedia &amp; Video
---

### Post by arcinthesky on 2006-11-23
Hi, I am a fresh-starter for linux.
I have 64MB Radeon 8500 SE on AGP 4x. I am currently dual booting linux and Windows XP. Thus I know my video card works completely fine.

It has been three days now that I have been trying to get fglrx to work on ubuntu 6.10 (Edgy). 

After installation
I have tried changing xorg.conf and set my device to fglrx instead of ati

I have followed both methods of this guide
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

and I still get the same error.

I start Ubuntu (GNOME session as default)
I login, and after 20-30 seconds everything else would freeze except my mouse cursor, I can move the mouse cursor but nothing else will work. Then I reboot and login again, it would freeze right after naturalis is loaded.

Yes before it freezes, I checked fglrxinfo and it displays the information about my ATI Radeon 8500 DDR Generic currently
As well direct rendering was on.

I have also completely uninstall fglrx and then installs the one on ati.com for my display card (8.28.8) and it installs completely.

I still get the same error. Please someone help me ](*,) ](*,)

---

### Post by DreamerHxC on 2006-11-24
I have the same error and I still haven't fixed it
[http://ubuntuforums.org/showthread.php?t=305409](http://ubuntuforums.org/showthread.php?t=305409)

---

### Post by pay on 2006-11-24
You could try the opensource radeon driver.

---

### Post by arcinthesky on 2006-11-24
Yes the open source driver does work, but really the performance i get is not as great as I do on videos, such as video playback on VLC. I don't see why my card would not work since the driver supports it. Thus please help to make my ubuntu experience better :neutral:

---

### Post by arcinthesky on 2006-11-24
Is there a way to install older fglrx versions? like 8.26.18? If yes, can anyone of you provide me with steps? Because edgy does not support those older drivers when i try to build them.

Of course i tried --buildpkg ubuntu/dapper
After i installed and reboot, it says fglrx is not found and wouldn't start X.

---

