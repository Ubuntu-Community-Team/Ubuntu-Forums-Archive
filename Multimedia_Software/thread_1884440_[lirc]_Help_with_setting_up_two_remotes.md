---
title: "[lirc] Help with setting up two remotes?"
date: 2011-11-21
forum: Multimedia Software
---

### Post by emgee11 on 2011-11-21
Hi All,
 
I'm using XBMC Live on an Antec Fusion Black case with a Snapstream Firefly remote.
 
I know the easier thing to do is just use the RM200 remote that came with the case, but I'd like to use the Snapstream because it is RF.
 
Anyways, I'd like to get the volume knob on the case going as well. My understanding is that lirc supports only one IR device by default/out-of-the-box and that I need to link up additional devices to connect to the lirc device I have specified in my hardware.conf. Some sort of chaining using "listen" and "connect".
 
I've tried it out, but apparently I'm not linking it up right. For if I do irw stops showing button presses. If I remove my linkings, irw shows the button presses for my Snapstream.
 
Has anyone here configured lirc to deal with multiple ir devices? Any help/suggestions would be most welcome.
 
Thank you!

---

### Post by azmyth on 2011-11-21
You basically need to run two instances of lirc. You need to modprobe the driver and when this happens a new lirc socket is created. You specify the driver and the location of the socket and the pid file for each remote and you will have two instances of lirc running.

see here

[http://www.lirc.org/html/configure.html](http://www.lirc.org/html/configure.html). You probably don't need the listen and connect statements in the examples.

---

### Post by emgee11 on 2011-11-22
Hi azmyth
 
I'll take a look at that and see if I can figure it out (new to ubuntu/linux).
 
Thanks.

---

