---
title: "BusyBox v1.1.3 (initramfs)"
date: 2007-12-26
forum: Mythbuntu
---

### Post by Alef Auman on 2007-12-26
When I try to install mythbuntu 7.10 I get the following message:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

I've found an interesting link which is maybe also my problem:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156428](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156428)

I'm using also a seagate harddisk ST320413A.

Is it possible to get a new iso file for this or can you explain me step by step how to do this?

When hitting Ctrl+Alt+F4 I get the following message:
cp : unable to open /root/var/log: No such file or directory
mount: mounting /root/dev on /dev/.static/dev failed: No such file or directory
...
...
target filesystem doesn't have /sbin/init

---

### Post by Alef Auman on 2007-12-27
With the version Edgy I don't have this problem

---

### Post by tonyr1988 on 2008-01-23
I have the same problem - have you found a solution yet?

....and Mythbuntu didn't have an Edgy version, right?

---

### Post by DuncanG on 2008-01-23
I have the same problem on CD install of 7.10 (graphical).
Gigabyte GA-MA69GM-S2H, AMD BE-2350, 1GB RAM
Samsung 1TB SATA
I have disabled the floppy drive and HPET. Before that it hung on "Running local boot scripts".

---

