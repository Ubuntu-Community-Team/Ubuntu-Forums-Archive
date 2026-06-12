---
title: "fglrx ati radeon 9000 WORKS easily now - a couple questions though"
date: 2006-10-04
forum: Multimedia &amp; Video
---

### Post by videodrome on 2006-10-04
Malac is a genius. 

I tried everything to make my ati radeon 9000 (it's a 128mb sapphire desktop agp card).

I read countess posts and websites and bug reports and whatnot. I did the "replace libGL.so.1.2 with an older version" thing. Then I got ELF errors with libGL.so.1. Then I messed around with the symlinks. Nada. 

I added things to the xorg file. I reinstalled the drivers. I reconfigured X. I blacklisted things. I messed with the agp drivers. I did it all. I followed the #1 howto at cchtml.com. Nothing.

Note I was scared away from doing the #2 method at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) because it says that the "new fglrx driver supports Radeon 9500+ (older cards will not work!)."

So no matter what I did, I either got the Mesa driver or nothing at all.

Then I followed Malac's post and it works. [http://www.ubuntuforums.org/showthread.php?t=197471](http://www.ubuntuforums.org/showthread.php?t=197471)

So this is what I did:
downloaded the older driver, put it in /usr/src/
set it's permissions to executable
used synaptic to install module-assistant
opened a root terminal and ran:
./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/dapper
dpkg -i *.deb
module-assistant prepare,update
rebooted

Note no messing with the xorg.conf, no modules, libGL.so.1.2, etc. It just works! Yeah! Finally.

loomis@p4-2ghz:~$ glxgears -printfps
10877 frames in 5.0 seconds = 2175.122 FPS
10740 frames in 5.0 seconds = 2147.847 FPS
10809 frames in 5.0 seconds = 2161.603 FPS
10771 frames in 5.0 seconds = 2154.070 FPS


* So my questions are: Is what I did any different than method #2 at cchtml.com?

* And will it break itself next time I update the kernel?

Thanks

---

