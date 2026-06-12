---
title: "Enabling WiFi management"
date: 2011-11-04
forum: Networking &amp; Wireless
---

### Post by mebss on 2011-11-04
Hi all !!
I just installed Kubuntu 11.10 on my Toshiba Satellite C-650D.
The problem is that I am not able to connect to a WiFi access point. I looked through the forum but none had the same problem since when I type 
[FONT=monospace]
[/FONT]
[B][SIZE=2]lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: b4:74:9f:e0:dd:20
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce  driverversion=3.0.0-12-generic firmware=N/A latency=0 multicast=yes  wireless=IEEE 802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:d0200000-d0203fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: c1
       serial: 00:26:6c:c2:aa:f3
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c  driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=24.201.79.157  latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:41 memory:d0100000-d013ffff ioport:2000(size=12:cool:
WARNING: output may be incomplete or inaccurate, you should run this program as super-user. [/SIZE][FONT=monospace][SIZE=2]
[/SIZE][/FONT][/B]
[FONT=monospace] 
This is what I get (*-network DISABLED for wifi). So I guess I just have to enable WiFi management... but as you can easily guess, I am a begginer :p
Note that Kubuntu (nor Ubuntu) is not 100% compatible with my laptop (maybe the new AMD shipsets are the problem), but WiFi should work since it worked on Ubuntu 11.04...
Thank you all.

EDIT : sorry I don't know how to emphasize the command text as other users do :(
[/FONT]

---

### Post by mebss on 2011-11-06
70 views and no reply... thank you anyway.

---

### Post by ashton112 on 2011-11-06
Sorry I cannot help, but this is a real problem. I have dual-boot Asus running Ubuntu 10.04. The problems seem common with the Atheros device. I installed and reinstalled so many versions of Linux and Atheros drivers, I finally had to give up, too much time wasted. It did work for as long time after removing 11.04 and installing 10.04, but the first time a 'system kernel update' occurred, right back where you are, with same symptoms. I will keep trying whenever I have time, and if I get any success, I'll post you a message. Good luck

---

### Post by pdc on 2011-11-07
if one googles on your device

[http://tinyurl.com/7q3nfz4](http://tinyurl.com/7q3nfz4)

you get hits such as this

[https://exain.wordpress.com/tag/rtl8188ce/](https://exain.wordpress.com/tag/rtl8188ce/)

he suggests

> The machine has rtl8188ce chipset, and the Realtek drivers available from Realtek&#8217;s website don&#8217;t work well. You just need to blacklist acer_wmi module

Edit /etc/modprobe.d/blacklist.conf and add

blacklist acer_wmi

Save and reboot. This won&#8217;t work if you&#8217;ve compiled Realtek drivers and installed them. It&#8217;ll work only in the default install. Here&#8217;s more detailed link -  [http://askubuntu.com/questions/53625/wireless-on-thinkpad-edge-e420s](http://askubuntu.com/questions/53625/wireless-on-thinkpad-edge-e420s)

if you look at the debian info on this device

[http://wiki.debian.org/rtl819x](http://wiki.debian.org/rtl819x)

it appears

> rtl8192ce (supported devices)

    Supports PCI-E devices based on the RTL8188CE and RTL8192CE chipsets.

    Introduced in Linux 2.6.38,7 enabled at linux-2.6 2.6.38-2. 

.......but that doesn't give you a specific action to take; it just seems to me the driver is built into the kernel 

the clearest is to do the blacklist specified in teh first post

if the above doesn't work 

go here [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

and supply as much of this information as you can; this forum runs on information; (others just run on love............)

---

### Post by mebss on 2012-02-22
Thanks to both of you :)
It apears that when I shutdown Windows with WiFi turned on, it works under linux, but when I leave Windows with WiFi off, it doesn't. So it takes the last state on Windows.
pdc, what you showed me is good to know, I'll mark the thread as solved.
Once again thank you and sorry for the late feedback.

---

