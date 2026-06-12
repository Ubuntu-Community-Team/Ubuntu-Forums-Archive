---
title: "VNC to main desktop :0"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by pcman312 on 2009-11-20
I am running Ubuntu 8.10 (haven't had the opportunity to upgrade since this is a machine at work, but I plan to soon). I have set it up so I can work from home using VNC, however, if I neglect to stop programs before I leave the previous day, there are programs running on another desktop. Now, this in itself isn't a problem because I can end the programs from the command line or the system monitor, or even reboot the machine remotely. What I'd like to be able to do is connect to the existing desktop that's running locally, rather than a new X desktop. Conceptually, I can see this in a couple of ways: set the vnc to point to :0 (which I haven't had much luck with) or set it up so the primary desktop is :1 and have vnc point to it as well. The second option probably has the same problems as :0 though.

I couldn't find any info on doing this, so if I missed it, a link would be appreciated :p

---

### Post by mr gibbs on 2009-11-23
Try this post by Veiloctane - [http://ubuntuforums.org/showthread.php?t=122402&page=55](http://ubuntuforums.org/showthread.php?t=122402&page=55)

It's worked perfectly for me (although I only use it on my internal network.:)

---

### Post by pcman312 on 2009-11-24
> **mr gibbs said:**
> Try this post by Veiloctane - [http://ubuntuforums.org/showthread.php?t=122402&page=55](http://ubuntuforums.org/showthread.php?t=122402&page=55)

It's worked perfectly for me (although I only use it on my internal network.:)
Thanks, I'll try that out next time I use VNC. Since I'm VNCing through a VPN to my work machine from home, it should recognize that I'm on the same network.

---

