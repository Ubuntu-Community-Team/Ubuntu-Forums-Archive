---
title: "How to get my surround sound working?"
date: 2008-04-26
forum: Multimedia Software
---

### Post by [DS]DragonSlayerz on 2008-04-26
I am running Ubuntu 8.04 Desktop

I have a Creative Live! 24 PCI sound card and 7.1 speakers. 

I have tried searching for thread on this forum to get it working but so luck.

Currently, only my front left & right speakers are working. On the volume setting, I only have the master volume.

I've already tried
> sudo gedit ~/.asoundrcand added 
> pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}


pcm.analog {
type plug
slave analog_slave;
}

pcm_slave.analog_slave {
pcm surround51;
format S32_LE;
}  

That didn't seem to work for me.

I also tried 
> gksudo gedit /etc/pulse/daemon.conf 
and changed
> default-sample-channels
i added = 8 and tried deleting that line but doesn't work.

Can someone please help me?

---

### Post by rockstar on 2008-04-27
similar threads

[http://ohioloco.ubuntuforums.org/showthread.php?t=693074](http://ohioloco.ubuntuforums.org/showthread.php?t=693074)

[http://ubuntuforums.org/archive/index.php/t-230323.html](http://ubuntuforums.org/archive/index.php/t-230323.html)

---

