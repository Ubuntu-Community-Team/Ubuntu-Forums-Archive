---
title: "Connection Problems: Wired and Wireless"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by NJ0E on 2009-10-14
Hello,

Just upgraded from 8.04 to 9.04.  Wireless was working, now it isn't.  Wired never worked, wasn't too concerned as I had wireless working.  

here is the output from ifconfig, iwconfig, lshw -C network and lspci:

nj0e@nj0e-laptop:~$ lspci

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



nj0e@nj0e-laptop:~$ lshw -C network

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

  *-network:0 DISABLED

       description: Ethernet interface

       physical id: 2

       logical name: vboxnet0

       serial: 0a:00:27:00:00:00

       capabilities: ethernet physical

       configuration: broadcast=yes multicast=yes

  *-network:1 DISABLED

       description: Ethernet interface

       physical id: 3

       logical name: pan0

       serial: 5e:c7:8a:42:04:5f

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

nj0e@nj0e-laptop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0b:db:99:0f:4f  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:7 


lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:4 errors:0 dropped:0 overruns:0 frame:0

          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

nj0e@nj0e-laptop:~$ iwconfig

lo        no wireless extensions.


eth0      no wireless extensions.


vboxnet0  no wireless extensions.


pan0      no wireless extensions.

Could someone please point me in the right direction to get either one of these working with out an internet connection to the down computer.  The one that I am posting on is a Winblows OS.  I can down load stuff, but obviously I can't get the Jaunty system connected to dwonloand anything.

Thanks

Joe

---

### Post by NJ0E on 2009-10-14
I have followed other posts for enabling the eth0.  editivng the /etc/newtork/interfaces file to add auto eth0 and also to specify one ip address as a static connection.  No luck.

Joe

---

### Post by NJ0E on 2009-10-15
Bump??

---

### Post by Iowan on 2009-10-15
What is currently in */etc/network/interfaces*? Were you originally trying to get DHCP address? How do you connect (modem, router, etc)?
I didn't see the wireless anywhere (maybe I just didn't recognize it). What kind is it?

---

### Post by NJ0E on 2009-10-16
Pardon the typing...  having to use two different computers to do this.  

/etc/network/interfaces is the following:
auto eth0
iface dth0 inet dhcp
auto l0
iface l0 inet loopback

When I run lsusb this is what I get:

Bus 001 Device 008: ID 201:3701 D-Link Corp. (hex) DWL-G120 Spinnaker 802.11B 
and then I have 3 entries for my usb root hub and then an entry for my mouse and the a last entry for the usb root hub again.

On my top panel there is a connection icon that when you mouse over and right click is had grayed out "Wired Network" and "device not managed" and then "VPN Connections" is active.

I ahve tried what I did in 8.04 to add PRISMA02.inf  -- but 9.04 says that the driver is invalid.

What is going on here?

Haven't gotten to the point of going back to windows, but it is fast approaching.  From what I see on the net 9.04 is supposed to see mmy wireless card natively  -- it doesn't give it power, yet my windows machine sees it and uses it just fine -- therefore I know it isn't the device.

---

### Post by Iowan on 2009-10-16
The wired might work - it is unmanaged because it is configured via */etc/network/interfaces*. I had a problem with DHCP on wired - [here]("http://ubuntuforums.org/showthread.php?t=1156441") is teh story.

---

### Post by NJ0E on 2009-10-17
Well, I tried it... HA no luck on it either.

NO wired, No wirless... HANDS IN THE AIR LIKE I JUST DON'T CARE.  

Reinstalled 8.04 by blowing out all partitions that I had, went back to ext3 with no partitions.  

Know that I can get wireless up and running in 8.04.  Guess I was never meant to have wired up on this computer (it is OLD)

Will get wireless up and then update from 8.04 to 9.04 via updater.

Wish the process well.

Joe

---

