---
title: "wireless not broken.. but slows down.."
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by struthmuffin on 2009-04-26
Hi, i am not really new to linux, but i am not at all close to a pro so hopefully someone can help me out with this....

i am running 9.04 ubuntu 64 bit.. everything is good for the most part... but my wireless slows down after the machine is on for a while.. (not sure for how long but lets say half a day or a day)  on a laptop by the way..

my transfer speeds on my local network should match what i can transfer in windows.. which is 2.5 megabytes/second.. but they are throttled to around 800 kilobytes/second when trying to transfer to another ubuntu machine over samba.  (this is the case always..regardless of reboot or not)

and if i do a speed test online when i start my machine both in windows and ubuntu it is usually a little bit above 10 megaBITS / second..  my isp provides 15 but I know i wont get that..   after some time with the computer on I run a speed test online again and I am only getting around 1 - 2 megabits / second..

does anyone know what i can do?

thanks in advance for any help or suggestions..

---

### Post by puller on 2009-04-26
What is your wireless card?

---

### Post by struthmuffin on 2009-04-26
when i run this command:  sudo lshw -C network   it says:

description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:42:9e:57
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.128 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg


i dont know if that answers what kind of card or just what it thinks it is... its a toshiba p100 laptop..

---

### Post by struthmuffin on 2009-05-04
nobody else having this problem?

---

### Post by cottfcfan on 2009-05-05
If you check the Forum a few of us are having the same problem.
But no one knows why or what the answwer is.
I hope someone can help!!

---

