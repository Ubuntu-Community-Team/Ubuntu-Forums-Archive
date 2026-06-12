---
title: "looking for files"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by daft_linux on 2010-01-10
hi
i've been checking a web page that talks about linux and networking, they mention some of these file paths:
[I]/etc/sysconfig/network-scripts/ifcfg-eth0
[/I][I]/etc/sysconfig/network-scripts/ifcfg-eth1

anyone knows where i can find [/I]these files in ubuntu, looks like they change name, the tutorial im looking at it's pretty old.
thanks

---

### Post by daft_linux on 2010-01-10
[FONT=Lucida Console]i neither can find the   [FONT=monospace][/FONT]ifconfig.c  file, ?
[/FONT]

---

### Post by pdc on 2010-01-10
there will be a utility called 

SEARCH

(in MENU/system ?? ....... not at ubuntu at present)

if you enter file names into that, it will try its hardest for you

---

### Post by chili555 on 2010-01-10
> **daft_linux said:**
> hi
i've been checking a web page that talks about linux and networking, they mention some of these file paths:
[I]/etc/sysconfig/network-scripts/ifcfg-eth0
[/I][I]/etc/sysconfig/network-scripts/ifcfg-eth1

anyone knows where i can find [/I]these files in ubuntu, looks like they change name, the tutorial im looking at it's pretty old.
thanksThose look like Fedora files to me. Ubuntu uses a different scheme. I think the closest is */etc/network/interfaces*. Please be very cautious about applying a Fedora fix to an Ubuntu system and, especially, a manual, hard-coded solution to an automated (Network Manager) system.

May we help you do whatever you are trying to do?

---

### Post by daft_linux on 2010-01-11
> **chili555 said:**
> Those look like Fedora files to me. Ubuntu uses a different scheme. I think the closest is */etc/network/interfaces*. Please be very cautious about applying a Fedora fix to an Ubuntu system and, especially, a manual, hard-coded solution to an automated (Network Manager) system.

May we help you do whatever you are trying to do?
hi and thank you. BTW i just would like to find those file as i like to look at C code, this is one of the reason i installed UBUNTU (to learn C networking), so those file are on Fedora ?
would fedora suit me better ? ( for someone who mainly wants to snicth thru code source files and program in C)

---

### Post by chili555 on 2010-01-11
These files:> /etc/sysconfig/network-scripts/ifcfg-eth0
/etc/sysconfig/network-scripts/ifcfg-eth1
are not C files, they are plain text files, similar to this:```
# Intel Corporation 82557/8/9 [Ethernet Pro 100]
DEVICE=eth0
BOOTPROTO=dhcp
HWADDR=00:D0:B7:08:09:BB 
ONBOOT=yes 
```There are plenty of C files to examine in Ubuntu. 

Fedora will probably not be better or worse for you; just different.

---

