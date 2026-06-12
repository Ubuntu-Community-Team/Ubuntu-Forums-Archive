---
title: "wpc11 v4 version 4 help needed PLEASE"
date: 2005-12-27
forum: Networking &amp; Wireless
---

### Post by centerprises on 2005-12-27
Hi I've followed everyone's posts and threads and seem to get very close but can't get it to work everytime.  I've used ndiswrapper for my linksys wpc11 ver.4  card with the realtek 8180 drivers here's what happens exactly.  Why is it not working when I do modprobe ndiswrapper.  Any suggestions would be greatly appreciated:

root@Debian2:/home/vw/wpc11# ndiswrapper -i NET8180.INF
Installing net8180
root@Debian2:/home/vw/wpc11# ndiswrapper -l
Installed ndis drivers:
net8180 driver present, hardware present
root@Debian2:/home/vw/wpc11# ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
root@Debian2:/home/vw/wpc11# modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/n et/ndiswrapper/ndiswrapper.ko): Operation not permitted
root@Debian2:/home/vw/wpc11# ndiswrapper -l
Installed ndis drivers:
net8180 driver present, hardware present
root@Debian2:/home/vw/wpc11# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

root@Debian2:/home/vw/wpc11# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:DA:EB:41:19
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:daff:feeb:4119/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:809 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:82434 (80.5 KiB)  TX bytes:11176 (10.9 KiB)
          Interrupt:11 Base address:0x4800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6231 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:565028 (551.7 KiB)  TX bytes:565028 (551.7 KiB)

---

### Post by fordfan753 on 2005-12-27
Maybe iwconfig just isn't picking it up, it's happened to me before. Do iwconfig wlan0 or iwconfig eth0 work at all?

---

### Post by centerprises on 2005-12-27
Yea it doesn't pick it up at all just shows a loopback and eth0 is a hard wire

---

