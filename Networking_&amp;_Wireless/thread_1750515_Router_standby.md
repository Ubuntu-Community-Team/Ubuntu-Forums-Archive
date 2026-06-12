---
title: "Router standby"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by alpetjr on 2011-05-05
It seems that after I updated ubuntu that I have a router problem. I have a Netgear WGR614 with my computer hardwired into port 1 on the router. When I shut the computer down the conection indicator on the router port 1 goes to standby (yellow). The ethernet indicator light on the back of the computer is off.If I unplug the cable from either the back of the computer or the back of the router the yellow light goes off. Anyone have any idea whats going on? Other than that there is no problems with the router or wireless conections. Thanks.

---

### Post by alpetjr on 2011-05-05
I tried resetting the router but that didn't help

---

### Post by Cheesehead on 2011-05-05
You haven't mentioned a problem.

For example, if the router port stayed yellow upon restarting your Ubuntu system and trying to reconnect, that would be a problem.

Youu also haven't told us what you have already tried. Unsuccesful results can be highly revealing...

---

### Post by alpetjr on 2011-05-06
I thought I did explain it. Instead of my wired port 1 shutting off when the computer is turned off, the port on the router turns yellow. I have a printer plugged into port 3 and another computer plugged into port 4. when the other computer and the printer is shut down those ports are turned off. when this computer on port 1 is shut off, port 1 goes to standby. The port 1 light turns yellow. It has never done that before.

---

### Post by tgalati4 on 2011-05-06
sudo apt-get install acpitool
sudo acpitool -w

Could be a kernel module change that leaves the network card powered to support wake-on-lan.

---

### Post by alpetjr on 2011-05-07
That didn't help. It is still doing the same thing. Any ideas? Thanks

---

