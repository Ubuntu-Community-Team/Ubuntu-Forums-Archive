---
title: "internet(not)"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by 5paul on 2009-05-21
hi there 
not sure where to put this,i just installed ubuntu 8.10 intrepid ibex on my acer extensa laptop
but i cant get on the internet with it?
in windows and i have used all versions i can connect straight away with this i cant,so i thought i ask first before i decide to go back to windows but there i have no problems.
i hope theres an easy answer because i have no idea i just managed to install it onto my d drive thats all the knowledge i have.
thank you.

---

### Post by dandnsmith on 2009-05-21
Are you connecting wirelessly (or trying to),
or is it an ethernet connection?

You need to be have assigned an IP address and routing details - can you say if this has happened (ifconfig in a terminal window will show the necessary detail)

---

### Post by spacesamurai on 2009-05-21
I know many times that the ether card driver is not installed. Maybe this could be a problem?

Some things you can test:
1. Are you able to ping the loopback (127.0.0.1)?
2. Are you able to ping the gateway?
3. Does the [ifconfig] command show your ether card is up?
4. Does [dmseg] show any hardware errors?

---

### Post by spacesamurai on 2009-05-21
You will have to give us more info to solve your problem. Can you describe how your network is setup? You connecting via a router? At any rate, please explain. Also, could you show us your [ifconfig] info.

```
$ ifconfig
```

---

### Post by superprash2003 on 2009-05-21
in your terminal type sudo dhclient eth0 ( where eth0 is the LAN interface ) and post output

---

