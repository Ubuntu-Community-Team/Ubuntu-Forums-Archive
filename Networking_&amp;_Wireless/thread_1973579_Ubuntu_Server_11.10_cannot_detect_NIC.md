---
title: "Ubuntu Server 11.10 cannot detect NIC"
date: 2012-05-05
forum: Networking &amp; Wireless
---

### Post by Strange1200 on 2012-05-05
Hello,

I am new to using Ubuntu and I wanted to start setting up a LAMP server. During my installation I got a message saying my NIC wasnt able to be detected and I would have to fix that after the installation... well ive been attempting this for the last few days now.

When I execute: sudo lshw -C network
nothing pops up. the Nic im using is an old SMC card which is installed in an ISA slot. I'm running Ubuntu server ver 11.10 on an old Dell P2/450 and I know its a functioning network cause because it worked when I was using Windows XP prior to formatting the drive.  
Anyway when I execute "sudo lshw | more" , I see this displayed under ISA:
description: ISA bridge
product: 82371AB/EB/MB PIIX4 ISA
vendor: Intel Corporation
physical id: 7
bus info: pci@0000:00:07.0
version: 02
width: 32bits
clock: 33MHZ
capabilities: ISA bus_master
configuration: latency=0

Ethtool is not installed nor can i run sudo apt-get install ethtool


any help would be great, thanks!

---

### Post by Strange1200 on 2012-05-07
I'm surprised. No one has any idea how I can get this resolved?!?!

---

