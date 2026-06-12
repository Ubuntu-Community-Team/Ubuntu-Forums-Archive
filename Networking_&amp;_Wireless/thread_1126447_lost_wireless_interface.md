---
title: "lost wireless interface"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by Magzee on 2009-04-15
Hi there.  I have a dell inspiron 8600 with a truemobile 1400 network controller. (Broadcom) bcm 4309.  Have been trying a few work arounds to get my wireless connection configured and connected through my home network (works on windows).  Not having much luck and now it would seem I have lost my wireless interface altogether.  Here is iwconfig and iwlist scan

```
magzee@ubuntudell:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

magzee@ubuntudell:~$ sudo iwlist scan
[sudo] password for magzee: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```

I am considering running a fresh install of Ubuntu Studio, but even if I do that, I will no doubt run into the same problem.

I have Windows XP on Partition 1 and Ubuntu Studio on partition 2.  No probs connecting through windows, although I had to manually set the ip addresses. The modem is Dlink modem/router DSL-G604T.

Anyone got any ideas???

Magz

---

### Post by William Anderson on 2009-04-24
Hi,

I have the same computer, a dell inspiron 8600, and the installed wireless card is recognised with the default install. now mine has an Intel PRO/Wireless 2100 card, but it connects to my home wireless as well as other nearby public wireless networks with no trouble.

Since none of the interfaces that are listed by iwconfig have wireless extensions, likely there is no driver loaded for the network interface. Including the systems dmesg output might be helpful. Open a terminal window and run the command "dmesg > dmesg.out" and attach the file dmesg.out to the message thread. 

Hope this helps,

William

---

