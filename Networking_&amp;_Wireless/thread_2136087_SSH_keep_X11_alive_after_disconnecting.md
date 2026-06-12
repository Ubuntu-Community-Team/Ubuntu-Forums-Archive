---
title: "SSH keep X11 alive after disconnecting?"
date: 2013-04-16
forum: Networking &amp; Wireless
---

### Post by lved on 2013-04-16
Hi.

is there any possibility to keep a x11 window alive or "move" the output to the server?
I use firefox to download a file, when I close the ssh connection firefox is terminated and the download is stopped.

I can't use workarounds like continue the download with wget because it's not an usual download,
its from a one click hoster with CAPTCHA protection.

Maybe someone has another idea than run xstart with vnc. :-|
Is there anything like screen or tmux?

---

### Post by TheFu on 2013-04-16
I use NX and routinely connect to it from different systems. Actually, my primary desktop is a VM running in a private cloud which is connected through NX. The OS runs 24/7 and I connect to it from multiple different locations and different client machines .... from in the same house to halfway around the world - seriously. Nepal, Seoul, Atltanta, Turkey, all work about the same.
NX provides a full GUI experience with only 2 limitations that I can see - audio support and video support are less than ideal.  For office-productivity apps and things like long downloads, it works perfectly.

---

### Post by lved on 2013-04-16
Seems to be a good solution. I'll give it a try.

---

### Post by TheFu on 2013-04-16
Well, you could just leave the ssh connection open too, but it seems that isn't an option for some reason?

VNC would be an option, but if you are doing this over the internet or WAN, then VNC needs a VPN to be secure.  NX uses ssh tunneling, so the security is already built-in.  VNC on a LAN would be easier to setup, probably, but I've found that VNC is about 2-3x slower than NX.

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) is the guide that I followed to get things working. Took about 10 minutes the first time, 5 minutes on other "servers" after that.  There are F/LOSS NX-clients, but those never worked all that well for me.  I gave up and installed the NoMachine NX-client last summer and haven't looked back. I can confirm that it works well on Wnidows7 x64 and both x32 and x64 Linux desktop systems.  

I haven't found a workable Android client, which is sad. NX seems to be depended on a working X/Server, which I guess Android doesn't have yet.

Good luck!

---

### Post by lved on 2013-04-18
Hi Fu,

the ssh connection is no problem as long as I'm using the computer. 
But when I'm done there's no reason to leave the computer on.
Imagine a turned on notebook with 3g in the trunk of a car, while you are driving home,
just to continue a download. :D

But it's really working great. The speed is incredible and the windows kept alive, like 
a shell via screen or tmux. 

I can fully recommend this solution. :)

Thank you.

---

