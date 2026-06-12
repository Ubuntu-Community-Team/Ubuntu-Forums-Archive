---
title: "Belkin N1 Modem/router"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by Foxfan100 on 2008-12-17
I've got a Belkin N1 device which is connected to PC by Ethernet cable (i.e no wireless involved).

It fires up fine from my Win XP system, but sporadically it doesn't get "seen" by my Ubuntu 8.10 set-up, so I have no connection. A swift restart may or may not bring it up, but it has a mind of its own.

This is more irritating than serious, but if anyone has any thoughts or suggestions about cause and/or fixes, I'd welcome them. I've done all the diagnostics but nothing tells me why it's "on/off" seemingly at random!

---

### Post by Skavenger0 on 2008-12-17
Have you tried restoring back to factory defaults incase its a firewall setting?

Have you got any unusual network controlling software? if so try removing it.

I had 2 similar issues:

1 Windows Dual boot was locking the network card when Ubuntu tried to access it. Make sure windows was disconnected properly/disable network card in windows.

2 My permissions were wrong so I couldnt access networking.

The 2 above issues should completly stop you accessing the network not periodically disconnecting.

Are you using DHCP? make sure the settings are correct.

---

### Post by Foxfan100 on 2008-12-19
Thanks.

I've tried pretty much everything, but no obvious cause for an intermittent problem.

I've just done a fresh install of 8.10 and so far this seems more consistent i.e. it fires up the network more often than not.

---

### Post by Foxfan100 on 2009-04-08
I first posted this in Dec 08 and it's now April 09. However, after a good run of connecting, I'm back to the same problem. I can connect fine from XP to the wired Belkin and out to internet. Quite often I can do the same from Ubuntu after rebooting to 8.10 from XP via GRUB. Occasionally I can achieve an immediate connection if I boot from machine start to Ubuntu but not always. All the right lights are up on the router, but Linux tells me that my network is disconnected.
The real drag is the sporadic nature of this. I would like to know 2 things:-
1) what the possible cause may be - nothing I've seen elsewhere seems to give me any idea of this.
2) what  the procedure or utility is in Ubuntu to connect or enable the network/router/adapter or whatever?

Thanks.

---

### Post by superprash2003 on 2009-04-08
could you post an output of **ifconfig** from the terminal..do you get an ip addresss always?

---

### Post by Foxfan100 on 2009-10-18
I've discovered that it's helpful to have "Connect automatically" for the wired ethernet checked in Network Manager!

I have looked through all the information on Network Manager, which doesn't tell me how to start it up manually. I presume that it has to be done via Console with:-

sudo ifconfig eth0 up
sudo dhclient eth0

I'd be grateful if anyone could confirm this.

Thanks,
Peter

---

