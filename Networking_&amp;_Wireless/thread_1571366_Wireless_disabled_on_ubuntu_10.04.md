---
title: "Wireless disabled on ubuntu 10.04"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by adrenalinche on 2010-09-09
Hello,
I after updating or something I wasn't able to connect to the internet(neither wireless, nor wired) anymore. I managed somehow with google-ing to fix the problem with the wired internet, but my wireless is still disabled. Here is what I got:

ifconfig
> 
eth0      Link encap:Ethernet  HWaddr 00:23:8b:bf:9a:84  
          inet addr:93.180.97.208  Bcast:93.180.97.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:febf:9a84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23921 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6551 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8217105 (8.2 MB)  TX bytes:1071830 (1.0 MB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:21:00:e7:82:71  
          inet6 addr: fe80::221:ff:fee7:8271/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5577 (5.5 KB)  TX bytes:5577 (5.5 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          inet6 addr: fe80::800:27ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:636 (636.0 B)


iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vboxnet0  no wireless extensions.


sudo gedit /etc/network/interfaces
> auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual


lspci
> 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)



I have the Broadcom STA wireless driver installed.(System -» Administration -» Hardware Drivers)

Any ideas what went wrong? I am a noob, so if you have any ideas please explain in details. Thank you ver much.

---

### Post by utilitytrack on 2010-09-11
First you need to remove [FONT="Courier New"]vboxnet0[/FONT] interface. If you such love VirtualBox, you can not do this; but in such case will be not possible to get working internet anyway. I ready to help how to do this.

1) wired network
Wich technology for to connect with your ISP you use? Ethernet? xDSL (seems to it)? I hope that's not a dial-up? :)

2) wireless network
please completely uninstall NetworkManager, and then we will have possibility to set up wireless network manually.

Also I suggest to turn off IPv6 protocol because it don't use and make unnecessary complexity. For this add [FONT="Courier New"]ipv6.disable=1[/FONT] to the kernel command line in file [FONT="Courier New"]/etc/default/grub[/FONT] (the result looks like: [FONT="Courier New"]GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1"[/FONT])

Next apply changes of bootloader configuration:
```
# update-grub
```

and reboot.

---

