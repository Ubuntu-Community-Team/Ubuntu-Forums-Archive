---
title: "No Net Connection after Update"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by Rick St. George on 2010-03-03
After updating Ubuntu v9.10, no longer have Network Access - No Network Connection! Even though nothing else has changed and the light on the ether card is on, indicating a signal.  

Any suggestions?
Thanks!

RSG

---

### Post by chili555 on 2010-03-03
We need more information, please.

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by Rick St. George on 2010-03-03
> **chili555 said:**
> We need more information, please.

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)


Network Scan:  Interface doesn't support scanning

Restart Network:  OK

No Machine Brand:  Custom Built

Net Controller:  RealTek RTL-8139

IFCONFIG:  RX Packets - 62 Errors; 1 dropped
                  TX Packets - 13 Errors; 0 dropped
                  Collisions - 0

Kernel Boot Msg.:  eth0 - No PIv6 routers present

Kernel Arch:  2.6.31-19 generic i686


Does this help?

---

### Post by chili555 on 2010-03-03
It does help. Is this machine dual-booted with Windows? Also, please post the result of this terminal command:```
dmesg | grep -e 8139 -e eth
```Thanks.

---

### Post by Rick St. George on 2010-03-03
> **chili555 said:**
> It does help. Is this machine dual-booted with Windows? Also, please post the result of this terminal command:```
dmesg | grep -e 8139 -e eth
```Thanks.

Cannot copy and paste since it is on another machine, but here is the gest ...

PCI Ethernet driver v1.3 (Mar. 22, 2004)
This is not an 8139C+ compatible chip,  use 8139too
8139too Fast Ethernet driver 8.9.28
RealTek RTL8139 at 0xd000, (mac add), IRQ 5
Link Up, 100 mbps, full-duplex, lpa 8x45E1
No IPv6 routers present


Other computers have access via the 4 port wireless Linksys Router.
Also - right clicking on Net Icon / Edit Connections / Wired / Edit Auto eth0
Wired Tab shows Mac and MTU = Auto; 
IPv4 Settings = Auto (DHCP);
IPv6 Settings = Auto

When changing the last two to Local Link Only - the Icon shows "Network Connection Active" but browser will not open any page.

Does this give anyone a clue?  Seems like the settings in the "Editing Auto eth0" are not right. Don't know how this got changed after an update, but I must be close to discovering the problem and getting back online.  Any and all help is appreciated.
Thanks!

---

### Post by chili555 on 2010-03-03
> This is not an 8139C+ compatible chip, use 8139tooPlease do:```
sudo rmmod -f 8139cp
```Now try the web and let us know if the behavior is improved. If this works, we need to edit a file to make it permanent.> Also - right clicking on Net Icon / Edit Connections / Wired / Edit Auto eth0
Wired Tab shows Mac and MTU = Auto;
IPv4 Settings = Auto (DHCP);
IPv6 Settings = AutoYou might have better luck with, if I remember correctly, IPv6 Settings = Ignore.

---

### Post by Rick St. George on 2010-03-03
> **chili555 said:**
> You might have better luck with, if I remember correctly, IPv6 Settings = Ignore.

THAT WORKED - Don't know why ... but, Thanks a Million ! ! ! 

RSG

---

