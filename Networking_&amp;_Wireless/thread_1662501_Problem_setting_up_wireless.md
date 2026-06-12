---
title: "Problem setting up wireless"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by dancrouchend on 2011-01-08
Hi, I am new to Ubuntu so please be gentle. :) I have just loaded Ubuntu on a Dell Inspiron 1300 laptop totally replacing Windows XP. The laptop was successfully connected wirelessly to a Netgear router previously. Having loaded Ubuntu, Network Manager cannot see any Wireless Networks. I have run a suggested code which came up with the Wireless adaptor or card is "Disabled", I think. Do I need to load a new driver? I believe that the hardware at issue is a Dell Wireless Card 1370 Mini PCI. I hope this makes sense and very grateful for any help. Cheers dancrouchend

---

### Post by dancrouchend on 2011-01-08
A little more information......

I tried.... sudo lshw -c network

and got the following back on the wireless interface.

* -network DISABLED
description: Wireless interface
physical id : 2
logical name: wlan0
serial: 00:14:a5:86:6c:99
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

Is this information helpful? Really appeciate any help. dancrouchend

---

### Post by bkratz on 2011-01-08
This really should give you what you need

[http://wireless.kernel.org/en/users/Drivers/b43#firmwareinstallation](http://wireless.kernel.org/en/users/Drivers/b43#firmwareinstallation)

---

### Post by dancrouchend on 2011-01-08
Sorted! Thanks very much for your help! dancrouchend

---

