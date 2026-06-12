---
title: "lost wired connection after update"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by fkh_63 on 2011-08-10
After I updated ubuntu 10.04.3 and restarted my PC, something weired happend and my wired connection was completely lost. I tried different things but it seems that I have lost my ethernet connection. I only have ethernet card and the interface was set to eth0 which is not recognized anymore. 

the /etc/network/interfaces includes the following commands, which btw I tried to play with a bit by commenting and uncommenting the lines (as mentioned in some forums) but was not helpful (but this is the original one):
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
------------------------------

also in /etc/udev/rules.d I deleted 70-persistent-cd.rules hoping that it would be automatically regenerated but it did not, that&#347; a pitty.
*********************************************

Here are some messages I get :
------------------------------------------------------------------------
sudo dmesg | grep eth
(I dont get anything here)
-----------------------------------------------------------------------
ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10344 (10.3 KB)  TX bytes:10344 (10.3 KB)
---------------------------------------------------------------------

lspci
00:00.0 Host bridge: Intel Corporation Device 0100 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation Cougar Point KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation Device 1502 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4)
00:1f.0 ISA bridge: Intel Corporation Device 1c4e (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68f9
03:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
---------------------------------------------------------------------------------------------------------------------

So I could somebody make any comments that what could be possibly going wrong? Thanks

---

### Post by bkratz on 2011-08-10
There is a lot of information about that card and 10.04 here

[http://ubuntuforums.org/showthread.php?t=1741686](http://ubuntuforums.org/showthread.php?t=1741686)

---

