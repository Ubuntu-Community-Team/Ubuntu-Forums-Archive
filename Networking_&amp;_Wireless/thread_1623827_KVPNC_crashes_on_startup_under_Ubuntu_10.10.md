---
title: "KVPNC crashes on startup under Ubuntu 10.10"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by erikvduyn on 2010-11-17
Title really says all, I installed KVPNC in Ubuntu 10.10 but I can't use it. It keeps crashing on startup. Who can help me out with this?

---

### Post by mxconsult on 2010-11-17
Have you tried running the VPN service via the command line? 

In my case I was having this very problem when trying to connect to a Cisco router with an IPSec VPN and the vpnc service. KVPNC started once, disconnecting every 50 or 60 seconds and reconnecting. However, the Cisco VPN client on a windows machine had no issues connecting to the same router from the same LAN on a Windows machine. I found out this thread, and it solved my problem, although I am restricted to invoking vpnc from the command line:

[http://www.ubuntugeek.com/how-to-setup-cisco-vpn-using-vpnc-ubuntu-jaunty-9-04.html](http://www.ubuntugeek.com/how-to-setup-cisco-vpn-using-vpnc-ubuntu-jaunty-9-04.html)

I would, however love to use the graphical interface.

---

### Post by erikvduyn on 2010-11-18
> **mxconsult said:**
> Have you tried running the VPN service via the command line? 

In my case I was having this very problem when trying to connect to a Cisco router with an IPSec VPN and the vpnc service. KVPNC started once, disconnecting every 50 or 60 seconds and reconnecting. However, the Cisco VPN client on a windows machine had no issues connecting to the same router from the same LAN on a Windows machine. I found out this thread, and it solved my problem, although I am restricted to invoking vpnc from the command line:

[http://www.ubuntugeek.com/how-to-setup-cisco-vpn-using-vpnc-ubuntu-jaunty-9-04.html](http://www.ubuntugeek.com/how-to-setup-cisco-vpn-using-vpnc-ubuntu-jaunty-9-04.html)

I would, however love to use the graphical interface.

That link would've been helpful, were it not for the fact that the very first wget is broken.

---

### Post by erikvduyn on 2010-11-19
Still not fixed, would like some help.

---

### Post by purct on 2010-12-08
I have the same problem,  however I find that if I run from terminal with sudo kvpnc it works.  

if I launch kvpnc from the icon, I am asked for password but then app crashes - if I then click on restart application button the kvpnc starts.

I was also getting a disconnection a few seconds after connecting to vpn but I found that Check connection status setup in my profile.  It was configured to 4 pings.   As soon as I disabled it my vpn stayed connected.

hope this helps!

---

### Post by YeeP on 2011-01-25
Exact same problem here. The only time I can get it to work is on first install. It will even connect. Then it crashes at every time I start.

The crash does read "The KDE crash handler", and I am running GNOME... Possible cause of the problem?

---

### Post by rockshore on 2011-04-08
> **purct said:**
> I have the same problem,  however I find that if I run from terminal with sudo kvpnc it works.  

if I launch kvpnc from the icon, I am asked for password but then app crashes - if I then click on restart application button the kvpnc starts.

I was also getting a disconnection a few seconds after connecting to vpn but I found that Check connection status setup in my profile.  It was configured to 4 pings.   As soon as I disabled it my vpn stayed connected.

hope this helps!

You little beauty! This worked a treat for me - thank you! ;)

---

