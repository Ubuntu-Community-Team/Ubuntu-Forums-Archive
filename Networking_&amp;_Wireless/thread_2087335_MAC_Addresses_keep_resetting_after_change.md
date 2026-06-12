---
title: "MAC Addresses keep resetting after change"
date: 2012-11-23
forum: Networking &amp; Wireless
---

### Post by LidlessEye on 2012-11-23
Hi All!

I'm on Ubuntu 12.10. I have several (12) USB to Ethernet Adapters which all show the same mac address assigned by the kernal, this is a problem since I'm using them to communicate with real switches to simulate a cisco lab w/ GNS3 and the switches think there are routing loops :O

That aside I've tried to set the mac addresses with both macchanger and ifconfig, and they do change but for about 5 minutes then they revert back to their mac's all being the same (except for 2 of them for some reason those two #7 & 8 seem to be keeping their assigned mac.

Now I have read that changing the macs via /etc/networking/interfaces would do the trick, but when I tried for just a single NIC my Ubuntu installation would not boot, hung and had to be repaired (remove that config) before able to boot again. I don't want this to happen, and I'm thinking perhaps the syntax was older/incorrect

This is what I used previously:

iface net1 inet dhcp
       hwaddress ether 01:02:03:04:05:06

2nd issue is that I've had to add entries to /etc/udev/rules.d to make sure the usb NICs are assigned interfaces based on their port, and upon reboot they are assigned the incorrect interface unless I unplug and replug them then they are assigned correctly. I'm sure there must be a way to refresh this with a script so I do not have to unplug/replug so if someone could enlighten me I would be eternally grateful!

If it helps here is what that config looks like:

4 Port PCI Bottom Port 1 (from left)
SUBSYSTEMS=="usb", ACTION=="add", KERNELS=="12-1:1.0", NAME="net1"

#4 Port PCI Bottom Port 2 (from left)
SUBSYSTEMS=="usb", ACTION=="add", KERNELS=="12-2:1.0", NAME="net2"

#4 Port PCI Bottom Port 3 (from left)
SUBSYSTEMS=="usb", ACTION=="add", KERNELS=="13-1:1.0", NAME="net3"

#4 Port PCI Bottom Port 4 (from left)
SUBSYSTEMS=="usb", ACTION=="add", KERNELS=="13-2:1.0", NAME="net4"



Thanks in advance I've been working on this several days and am at my wits end! :P

Cheers!
LidlessEye

---

### Post by Sergius14 on 2012-11-23
Edit this file:

```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```


It explains it self what to chache on that.


This definetelly work on Ubuntu Servers. I've done it several times. Give it a try !


Then do a:

```
service networking restart
```

---

### Post by LidlessEye on 2012-11-24
I've only been successful changing the name with 70-persistent-rules, and i copied what i have in that file in the first post. Any other ideas for statically assigning mac address?

---

