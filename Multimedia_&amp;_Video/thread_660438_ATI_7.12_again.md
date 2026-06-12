---
title: "ATI 7.12 again"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by mad_max0204 on 2008-01-06
First of all I want to say that theres much talk about this new driver and ATI problems under linux.
Good thing is that with this new driver "AIGLX is supported". I'm not too familiar about the whole linux thing but I try to learn ever day.
There is a good ATI 7.12 installation guide on [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").
I followed this guide (Method 2) and managed to install ATI drivers manually. I get about 10.000 fps in glxgear and desktop effects on full. Look nice and works good. Had to manually edit xorg.conf to get the 1680x1050 resolution on my 22" wide monitor.
When I open restricted driver manager it says that ATI driver is in use but the box is unchecked. Thats something thats mentioned in the guide above and its a good sign.
Now, problems are that I cant run compiz (I dont need it but its a good test). There is no /usr/sbin/compiz ffile/dir so I cant whitelist driver (also mentioned in the howto).
Second problem is with cedega. I never got it to work on this rig. Last time I tried I got 3d accel. but no opengl. Now I dont get opengl and 3d. Are there some thing I need to install/set to get this to work.
Also there are some problems with video.
One more thing, after installation in settings for Screens and drivers (is this right name) I have a blank on screen name and 640X480 resolution.

Anyone with X1950pro and Ubuntu 7.10_x64 managed to get everything to work ??

Thanks

---

### Post by Yellow Pasque on 2008-01-06
-It's /usr/bin/compiz, not sbin

-I wouldn't worry about the screen and driver dialog. Use ATI CCCLE, or sudo dpkg-reconfigure -phigh xserver-xorg failing that.

---

### Post by mad_max0204 on 2008-01-07
sorry twas a typo.
yeah I did run ATI cccle but there was no info on monitor either. funny thing is that it works.
any idea on getting Opengl and 3d in Cedega ??

---

