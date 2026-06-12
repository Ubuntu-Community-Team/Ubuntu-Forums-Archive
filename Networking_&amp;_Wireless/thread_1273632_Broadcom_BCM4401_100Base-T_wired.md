---
title: "Broadcom BCM4401 100Base-T wired"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by NJ0E on 2009-09-23
Hello all.  I have been looking at all the posts for this card.  

My system --
Dell 5150 laptop.
Wireless thru usb works fine
wired inop.

Here is the returns form ifconfig:
nj0e@nj0e-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:db:99:0f:4f  
          inet6 addr: fe80::20b:dbff:fe99:f4f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:250 (250.0 B)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9433057 (9.4 MB)  TX bytes:9433057 (9.4 MB)

wlan0     Link encap:Ethernet  HWaddr 00:0f:3d:4b:ae:c6  
          inet addr:192.168.0.147  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:3dff:fe4b:aec6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:265380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:132345814 (132.3 MB)  TX bytes:15595840 (15.5 MB)

And the return from lshw -C Network:

nj0e@nj0e-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:99:0f:4f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:0f:3d:4b:ae:c6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+prisma02 driverversion=1.53+GlobespanVirata,11/11/2003, ip=192.168.0.147 multicast=yes wireless=IEEE 802.11g

And from lspci:
nj0e@nj0e-laptop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller


As I stated I have wirless connection just fine.  When I try to use my wired connection it won't connect.  

I am using Wicd for the conneciton tool instead of network manager as I had problems network manager vs my wirless card.

I would apprieciate all help

Joe

---

### Post by NJ0E on 2009-09-24
Bump???

---

### Post by Ayuthia on 2009-09-24
You don't have the ssb module blacklisted, do you?  The ndiswrapper module has some problems with the ssb module so usually people recommend that it gets blacklisted.  To enable the b44 module with ndiswrapper, the normal recommendation is to do the following:
```
sudo modprobe -r b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44
```

If it does work after that, you might check and see if the b44 or ssb module is blacklisted.  If it is not, you can always add the above commands in /etc/rc.local wtihout the leading sudo.

Hope that helps.

---

### Post by NJ0E on 2009-09-27
Did all the commands -- haven't had a chance to restart yet.  Also tried fo find the /etc/rc.local folder.  was unabale.  located multiple folders /etc/rc.*** but no /rc.local  Any ideas -- (have yet to search hidden in the /etc folder.

Thanks

---

### Post by Ayuthia on 2009-09-27
The /etc/rc.local file should be there and it should not be hidden.

When you run the modprobe commands, you should not reboot.  They are temporary commands that only last for that session.  When you run them, you should disconnect from your wireless and try to connect with your wired card.

---

### Post by NJ0E on 2009-09-30
No connection wired, wireless went right thru.  Also no  /etc/rc.local.  Any ideas?

---

