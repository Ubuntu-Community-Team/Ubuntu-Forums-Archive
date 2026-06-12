---
title: "static ips and lan gaming"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by seret on 2009-03-23
Hey

My problem is that the wireless network our school provides is not for gaming so we have to resort to setting up our own wireless. The problem is that since im the only one using ubuntu while everyone else uses vista.

so how do i set a static ip and connect to a local network created in vista.
I have tried my way around the "NetworkManager Applet 0.7.0" but to no avail. So is there an easy way to temporary set a static ip and connect to such a network? 

With kind regards Seret

English is my second language, therefore my spelling is subpar.

---

### Post by MaindotC on 2009-03-23
Here's how to change your ubuntu machine's ip address from the command line:

[http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)

I'm curious as to why this is such a task compared to Vista...

---

### Post by seret on 2009-03-23
Hey 

Thanks for the quick reply. Im looking for a solution thats only temporary, either resets on reboot or is easy to toggle back?
Im using an atheros wireless card (i am using madwifi's support)
all it says in interface is 
auto lo
iface lo inet loopback

and when i have changed my ip how do i connect to the wireless?

With kind regards Seret

---

### Post by MaindotC on 2009-03-23
When you want to go back to dhcp just type:
```

sudo dhclient

```
When you have changed your IP you still connect to your wireless access point just you would have before - just find the SSID and connect to it.

---

### Post by BkkBonanza on 2009-03-23
You may want to install Wicd instead of using Network Manager. It can be installed using Synaptic and will replace NM. It has various options in it's gui for static ips and dns stuff. I found it much more flexible as did others around here.

It allows setting static ip on a profile basis so that only certain connections will use that.

---

