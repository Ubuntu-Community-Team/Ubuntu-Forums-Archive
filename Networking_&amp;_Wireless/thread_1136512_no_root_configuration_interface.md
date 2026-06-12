---
title: "no root configuration interface"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by Ole Juul on 2009-04-25
We just upgraded from Kubuntu 8.10 to 9.04 and (among other things) there is now no network connection. We do not know how to use the GUI interface because it does not allow root access. Is there a way around this or does 9.04 need to be configured by editing files?

(PS I am the go-between because the other person's network is now broken)

---

### Post by Ole Juul on 2009-04-25
Even if someone could suggest how to get a root console in this 9.04 it would be helpful. At this point we're desperate to be able to use this computer.

---

### Post by Iowan on 2009-04-25
Unless something has changed, I presume you should still be able to use **sudo** for root (terminal) access. My machines don't have enough horsepower for Kubuntu, but I suspect */etc/network/interfaces* is the configuration file... and **ifconfig -a** should show current status.

---

### Post by abn91c on 2009-04-25
right click on the lower bar add widgets, then select the network management widget, right click on the widget>manage connection then set up you network ssid, security, dont forget to check the "connect automatically" box in the last screen before clicking save and connect

---

### Post by Ole Juul on 2009-04-25
This is not wireless. Just a simple static setup like we've always had here.

Thanks Iowan, I'd forgotten that it was sudo and not su. (sigh) I got it now. Sudo works and I can confugure the network by hand. There's plenty of how-tos on that. :) We're back on the net. W00t!

I'll look into the real problem later. There is no root terminal like the previous version of Kubuntu, but sudo works. So that part is OK. The part that is really broken is the GUI interface for system settings which doesn't have root access. Networks now have to be configured by hand. People uncomfortable with the command line are going to be unhappy with 9.04 :( I hope other old folks and non-professional users like us don't try to upgrade - they'll get a big surprise!

---

