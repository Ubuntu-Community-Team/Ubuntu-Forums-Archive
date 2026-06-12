---
title: "Multi network card problems."
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by jakkals on 2009-04-07
Hi there!

I have a problem with multiple LAN-cards on Ubuntu 8.04 LTS Server Edition.

Three LAN's on the machine -  the onboard and 2 x Realtek 8-series cards. During installation the cards are detected correctly, eth0 is identified correctly and it obtains a dhcp lease from my internal network router. Installation proceeds, mirror is scanned and no problem. Once completed and after reboot there is simply nothing working. During boot, when loading the network, quite some time goes by before the boot process proceeds. ifconfig shows eth0 with no dhcp lease obtained and therefor no LAn access. Needless to say the other two cards are nowhere to be seen. Going into /etc/network and manually editing 'interfaces' produces all sorts of weird responses when trying to restart the network. However, taking the two PCI-cards out I am able to obtain a dhcp-address and connect to the machine.

Any ideas?

---

### Post by Iowan on 2009-04-07
What's in the */etc/network/interfaces* file?

---

### Post by lensman3 on 2009-04-08
This is not a very helpful reply, but you want to force the Ethernet cards to belong to each cards unique NIC address.  During boot, the "dmesg" command will show the Ethernet cards NIC, but after the boot.  "lspci" didn't show the NIC number.  

The hardware is forced to a device eth0, eth1, eth? in the /etc/modprobe.d directory.  The file modprobe.conf.dist has a line it that sets the hardware to the interface.  Interrupts can also be set, but that is very specific to the drivers.

Hope this helps and gives you a place to look.

---

### Post by jakkals on 2009-04-08
Hi all.
Thanks for the responses. Every litlle bit always helps and is really appreciated.
I , at the moment, do not really realise what it is I did but it WORKS!
I am going to post a full description of what happened, the different error messages I got and how it was resolved as soon as I can write it up.
I hope it will be to the benefit of others with the same or similar problem

---

