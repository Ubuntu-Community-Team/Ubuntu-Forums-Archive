---
title: "zbox nd22 ethernet (forcedeth) problem"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by morinpatmorin on 2011-04-26
I just bought 4 zotac zboxhd-nd22-u's (for a lab), and I'm having problems with the ethernet adapters.  For some reason eth0 (which is connected at 1gbps) seems to just stop working occasionally and then comes back.  Since these rely on nfs and nis, this makes the machines unusable.

I've tried 10.04.2 and 10.10 32-bit and 64-bit versions with the same results.

dmesg isn't very helpful.  The only thing related to networking is

rt_ioctl_giwscan. 4(4) BSS returned, data->length = 2343

but I think this is from the wireless card, which isn't being used.

Has anyone else had this problem?

An lspci -v for these machines is available here:

[http://www.zotacusa.com/forum/topic/4161-zboxhd-nd22-u-hardware-inventory/](http://www.zotacusa.com/forum/topic/4161-zboxhd-nd22-u-hardware-inventory/)

Thanks for any help you can give.

Pat

---

### Post by uncaspi on 2011-04-26
Perhaps the driver is unstable for 1gbs transfer. Let's see
sudo lspci -nn | grep Ethernet

---

### Post by morinpatmorin on 2011-04-26
> **uncaspi said:**
> Perhaps the driver is unstable for 1gbs transfer. Let's see
sudo lspci -nn | grep Ethernet

rootlocal@gauss:~$ sudo lspci -nn | grep Ethernet
[sudo] password for rootlocal: 
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP79 Ethernet [10de:0ab0] (rev b1)

You may be right.  I brought one home and I haven't experienced the problem yet on my home network (running at 100Mbps).  Unfortunately, lowering the speed isn't a workable option though.

I'm curious to see if anyone else has experienced this problem.

Pat

---

### Post by uncaspi on 2011-04-26
The hex code points to forcedeth driver in 
/lib/modules/`uname -r`/modules.pcimap

---

### Post by morinpatmorin on 2011-04-26
Everything I read about the forcedeth driver says this should just work fine, but it doesn't.  It does on my older ion machine even though it seems to have exactly the same Ethernet hardware:

rootlocal@gauss:~$ lspci -nn | grep Ethernet
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP79 Ethernet [10de:0ab0] (rev b1)

morin@miniscule:~/$ lspci -nn | grep Ethernet
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP79 Ethernet [10de:0ab0] (rev b1)

---

### Post by uncaspi on 2011-04-26
Maybe your distro are newer with another version of the driver. You could try to copy forcedeth.ko from the older box if the two boxes have same kernel version.

---

