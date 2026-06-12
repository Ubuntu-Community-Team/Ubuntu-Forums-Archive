---
title: "Wireless not working in 12.04 (Intel Pro 2200BG card)"
date: 2012-05-18
forum: Networking &amp; Wireless
---

### Post by johnchocolate on 2012-05-18
Hi, thanks in advance to anyone who can help with this:

My wireless card (Intel Pro 2200BG) no longer works now I've installed Lubuntu 12.04. It worked fine under Ubuntu 10.04 and still does under Windows.

I'll try and post some relevant information, having read the forum guide. Thanks again.


robert@robert:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no




robert@robert:~$ sudo lshw -C network
[sudo] password for robert: 
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:5d:44:e3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:5 memory:98180000-98180fff
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 13
       bus info: pci@0000:00:13.0
       logical name: eth0
       version: 01
       serial: 00:08:02:97:6a:a4
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=5705-v3.14 ip=192.168.1.112 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:10 memory:98000000-9800ffff memory:30000000-3000ffff



robert@robert:~$ lspci -nn | grep 2200
00:09.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)



robert@robert:~$ ls -al /lib/firmware | grep ipw
-rw-r--r--  1 root root  209190 Apr  2 20:51 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 Apr  2 20:51 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 Apr  2 20:51 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 Apr  2 20:51 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 Apr  2 20:51 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 Apr  2 20:51 ipw2200-sniffer.fw

---

### Post by chili555 on 2012-05-18
Network Manager is designed to disallow a wireless connection if wired is connected, which it is:> ip=192.168.1.112 latency=64 link=yes Please detach the ethernet cable. Now click the NM icon and try to connect. Do you see your network? Does it try to connect? Any clues here?```
dmesg | grep ipw
```

---

### Post by johnchocolate on 2012-05-18
Hi there.

Thanks for your very quick reply - much appreciated.

Good point about removing the ethernet cable - stupid mistake. It didn't resolve the problem by itself though - I had to use the command sudo modprobe ipw2200 which I picked up from another forum. This seems to have kicked the card into life. I am still a bit confused, as I have tried this before (with the cable unplugged) and it didn't work.

The only remaining issue is that I have to reissue this command each time I restart the computer. Is there a way of making it permanent?

The dmesg output in case its still relevant:
robert@robert:~$ dmesg | grep ipw
[   72.713148] libipw: 802.11 data/management/control stack, git-1.1.13
[   72.713155] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   72.742776] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   72.742789] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   72.743417] ipw2200 0000:00:09.0: PCI INT A -> Link[C0C8] -> GSI 5 (level, low) -> IRQ 5
[   72.743477] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   72.870794] ipw2200: Radio Frequency Kill Switch is On:
[   72.877984] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

Thanks very much again for your help.

---

### Post by chili555 on 2012-05-18
> use the command sudo modprobe ipw2200 which I picked up from another forum. This seems to have kicked the card into life. I am still a bit confused, as I have tried this before (with the cable unplugged) and it didn't work.

The only remaining issue is that I have to reissue this command each time I restart the computer. Is there a way of making it permanent?Please try this:```
sudo su
echo ipw2200 >> /etc/modules
exit
```Please reboot with the ethernet cable detached and let us have your report.

---

### Post by johnchocolate on 2012-05-19
Ok, that seems to have done the trick. Thanks for your support - first time I've used the forum and I'm very impressed.

---

### Post by chili555 on 2012-05-19
I'm glad it's working and thanks for your kind comments.

---

### Post by c9jeff on 2012-06-24
Thanks @chili555 you are the wireless master.  This helped get the wifi connection back up quickly on this old dell Latitude D610 after updating  to 12.04.

---

