---
title: "No network connection after LXDE installed"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by bcz on 2010-04-23
I was running Ubuntu 9.04 Gnome version and installed LXDE with the lxdnm network manager.  (by default, this would not have been loaded.. )

LXDE loaded up without network support

The network tools applet shows the loopback interface active

ETH0 is inactive.  How do I activate it..  Any ideas

Also a network device PAN0 is shown, also inactive..  Any ideas what this is?

Synaptic loads.  Can I revert back to my original desktop

Rgds Bill

---

### Post by bcz on 2010-04-23
I was running Ubuntu 9.04 Gnome version and installed LXDE with the lxdnm network manager.  (by default, this would not have been loaded.. )

LXDE loaded up without network support

The network tools applet shows the loopback interface active

ETH0 is inactive.  How do I activate it..  Any ideas

Also a network device PAN0 is shown, also inactive..  Any ideas what this is?

Synaptic loads.  Can I revert back to my original desktop

Rgds Bill

---

### Post by mikewhatever on 2010-04-23
You should still be able to select Gnome at login, thus effectively reverting to the original desktop.

---

### Post by Iowan on 2010-04-23
I'm completely unfamiliar with LXDE and even less familiar with lxdnm. Have you tried defining your interface in */etc/network/interfaces*?
(What's there now?)

---

### Post by adam814 on 2010-04-23
If it's still installed you could try starting up nm-applet (the GNOME NetworkManager applet).

If it's just a wired interface you're concerned with you could always try this:
```
sudo ifconfig eth0 up && sudo dhclient eth0
```

As for pan0 it's most likely a bluetooth transceiver.

---

### Post by bcz on 2010-04-24
Revert to Gnome desktop and have same problem.

However I type as follows:

ifconfig -v eth0 192.164.5.25 up
route add default gw 192.165.5.1 eth0

I can now ping my ISP as ping 210.x.y.z

ping [www.ispname.net.au](www.ispname.net.au) fails, so I assume I must manually configure my DNS server.  How do I do this?

Rgds Bill

---

### Post by bcz on 2010-04-24
Thanks to all

What I did was change my session back to gnome on reboot

ifconfig -v eth0 xx.yy.zz.5 up
route add default gw routerAddr etho

which got basic internet access, but no DNS

dhclient eth0

which got it working properly so I can now reinstall gnome network manager.

Then maybe try LXDE again

Rgds Bill

---

### Post by bcz on 2010-04-24
Thanks to all

What I did was change my session back to gnome on reboot

ifconfig -v eth0 xx.yy.zz.5 up
route add default gw routerAddr etho

which got basic internet access, but no DNS

dhclient eth0

which got it working properly so I can now reinstall gnome network manager.

Then maybe try LXDE again

Rgds Bill

---

### Post by Iowan on 2010-04-24
Threads merged - duplicate post deleted.
Sounds like you're making progress...
Good luck!

---

