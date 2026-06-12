---
title: "PPTP and remote desktop"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by digitography on 2011-01-03
I don't even know if this is possible, but here goes.

I have a computer at home that I would like to connect to using remote desktop, so I can take control.
I know I could do this with something like gotomypc, but there is no version for Linux.
So is it possible to do this using PPTP?
suggestions always welcome.

---

### Post by PatchesTheCaveman on 2011-01-03
The software that accomplishes this on Linux is called VNC.  A server program comes installed by default on most Ubuntu installations.  Just go to System > Preferences > Remote Desktop to configure it.

If for some reason you don't have that, install the *vino* package.

You can use any VNC viewer on Windows, Mac, or Linux to access the connection once you have configured it.

I recommend the TightVNC viewer on Windows:  [http://tightvnc.sf.net/](http://tightvnc.sf.net/)
and Chicken of the VNC on Mac:  [http://cotvnc.sf.net/](http://cotvnc.sf.net/)
But everyone has their own preferences.  :-D

---

### Post by endotherm on 2011-01-03
ok, first and foremost, VNC is NOT safe to expose to the internet, out of box. 

PPTP is a VPN protocol, so yes it would work, but you need to configure a VPN server on your gateway. after establishing a VPN tunnel, you should be able to do what you want. 

an easier alternative is to use SSH. like a VPN, ssh can tunnel traffic, and uses strong authentication and encryption. 

here is a tutorial on connecting to VNC over SSH:
[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

there is also FreeNX, which I think is far superior to VNC. it uses SSH built-in and there are free clients for windows and linux. 
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

