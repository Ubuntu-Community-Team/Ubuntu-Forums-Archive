---
title: "problem or not with wireless"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by Cyrusb on 2010-05-31
Hi.....
I have problem with my D-Link airplus G dwl g510 PCI wireless card.
When I boot Ubuntu 9.10 live cd it works fine.
But when I install Ubuntu card works only the first when i boot the system of my hard.
After first reboot it says that the DEVICE NOT MANAGED. 
I am new in using Linux. I don't want to quit and go back to windows:cry:,please HELP.

---

### Post by mikewhatever on 2010-05-31
Can you post the output of the following: **sudo lshw -C network**.

---

### Post by Cyrusb on 2010-06-01
sorry i didn`t know what to do.
sudo lshw -C network
 *-network               
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: wmaster0
       version: 00
       serial: 00:22:b0:6f:88:bd
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:ee000000-ee007fff

Any suggestions? TNX

---

### Post by mikewhatever on 2010-06-01
This is a little odd. The drivers seems to be loaded, but I am baffled by the interface name, wmaster0.:confused:

---

### Post by Cyrusb on 2010-06-03
I solve the problem. 
In the /etc/NetworkManager/nm-system-settings.conf
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false   ------- change to true    and now i have working network.
I fond this somewhere on this forum but didn't work for that guy but worked for me........

---

### Post by Cyrusb on 2010-06-03
Thank you for interesting for my problem,  [mikewhatever]("http://ubuntuforums.org/member.php?u=160645")

---

