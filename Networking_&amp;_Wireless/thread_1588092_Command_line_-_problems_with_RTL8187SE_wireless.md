---
title: "Command line - problems with RTL8187SE wireless"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by edsmaffs on 2010-10-04
Hi.

I've just installed the 64-bit command-line version of Maverick from the Alternate CD, and am having trouble getting the wireless all configure. I've already installed wireless-tools via a *.deb archive.

My card normally uses the rtl8187se or the r8187se module to run. I've checked with "lshw -C network" and it is there under the wlan0 interface - however, it says that it is using the driver "r8180".
This isn't what I would expect given how it was working under the Desktop version.

I've also tried this series of commands (sudo omitted but I did use it):
```
ifconfig wlan0 down
dhclient -r wlan0
ifconfig wlan0 up
iwconfig wlan0 essid NETGEAR
iwconfig wlan0 key XXXX-XXXX-XX
iwconfig wlan0 mode Managed
dhclient wlan0
```

The final command fails to find an IP address for the computer - none of the other commands give any error message.

I think the problem here is the fact that it's using a different driver - is there an easy way for me to change this?

---

### Post by edsmaffs on 2010-10-04
Also worth mentioning on the driver front:

r8187se showed up when I tried "lsmod". Neither r8180 nor rtl8187se showed up.

---

