---
title: "Can't connect to internet on re-install of 10.04"
date: 2011-02-11
forum: Networking &amp; Wireless
---

### Post by CT Husky on 2011-02-11
I am running a Ubuntu-only Dell Inspiron 1545 laptop.  Upgraded to 10.04 several months ago, and no problems until last week. (Possible cause: my daughter turned on the laptop, and then plugged in the laptop while it was still booting up; thereafter I was never able to get past the sign-in screen; it would keep returning to the sign-in screen, with an error message, I forget exactly what it was.)

I was able to run from a live disk okay, and was able to get out all my documents to backup.

I then did a reinstall using a CD. Everything seemed to go fine.  Computer boots up nicely, and all the programs seem to work fine.  

However, I can't get connectivity.  When I run apt-get update or try to load a driver, I get errors along the lines of "Failed to fetch" and "Could not resolve 'us.archive.ubuntu.com'


I looked in many forums, I'm sensing it is a card or driver issue or similar, and so I am posting outputs from the following commands:

ifconfig
ifconfig -a
lspci -nn
lshw -C Network
uname -rm
dmesg | grep -e wlan -e eth

and also: dhclient eth0 

Any help greatly appreciated; I have been using Ubuntu at home for a while, but really am not good or sophisticated at this at all, so my apologies, but it's best to talk to me like I'm a third-grader!

ted@ted-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:ae:3b:26:9b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth0:avahi Link encap:Ethernet  HWaddr 00:23:ae:3b:26:9b  
          inet addr:169.254.6.208  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

ted@ted-laptop:~$ 
ted@ted-laptop:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:23:ae:3b:26:9b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:18 

eth0:avahi Link encap:Ethernet  HWaddr 00:23:ae:3b:26:9b  
          inet addr:169.254.6.208  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB) 

pan0      Link encap:Ethernet  HWaddr ee:de:63:3c:68:86  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

ted@ted-laptop:~$ 

ted@ted-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:ae:3b:26:9b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth0:avahi Link encap:Ethernet  HWaddr 00:23:ae:3b:26:9b  
          inet addr:169.254.6.208  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

pan0      Link encap:Ethernet  HWaddr ee:de:63:3c:68:86  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ted@ted-laptop:~$ 

ted@ted-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:ae:3b:26:9b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth0:avahi Link encap:Ethernet  HWaddr 00:23:ae:3b:26:9b  
          inet addr:169.254.6.208  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

pan0      Link encap:Ethernet  HWaddr ee:de:63:3c:68:86  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ted@ted-laptop:~$ 

ted@ted-laptop:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07) 
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07) 
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07) 
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03) 
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03) 
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03) 
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03) 
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03) 
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03) 
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03) 
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03) 
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03) 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93) 
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03) 
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03) 
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13) 
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01) 
ted@ted-laptop:~$ 


ted@ted-laptop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network UNCLAIMED     
       description: Network controller 
       product: BCM4312 802.11b/g 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: cap_list 
       configuration: latency=0 
       resources: memory:f69fc000-f69fffff 
  *-network 
       description: Ethernet interface 
       product: 88E8040 PCI-E Fast Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       logical name: eth0 
       version: 13 
       serial: 00:23:ae:3b:26:9b 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes 
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256) 
ted@ted-laptop:~$



ted@ted-laptop:~$ uname -rm 
2.6.32-21-generic i686 
ted@ted-laptop:~$ 

ted@ted-laptop:~$ dmesg | grep -e wlan -e eth 
[    1.313610] sky2 eth0: addr 00:23:ae:3b:26:9b 
[  783.952791] sky2 eth0: enabling interface 
[  783.954642] ADDRCONF(NETDEV_UP): eth0: link is not ready 
ted@ted-laptop:~$ 

ted@ted-laptop:~$ sudo dhclient eth0 
[sudo] password for ted: 
There is already a pid file /var/run/dhclient.pid with pid 2146 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.1.3 
Copyright 2004-2009 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/) 

Listening on LPF/eth0/00:23:ae:3b:26:9b 
Sending on   LPF/eth0/00:23:ae:3b:26:9b 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
ted@ted-laptop:~$

---

### Post by P4man on 2011-02-11
Are you trying wired (ethernet) or wireless? The wired network controller seems to be not plugged in. If it is, can you check the cable and see if the leds change color when you plug it in?

The wireless may need drivers, but its easiest to install those if you have a wired connection. More info on your  wireless here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

(you have the BCM4312).

---

### Post by herdwick on 2011-02-11
It's trying to get an IP address on eth0 and failing :-

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1 
No DHCPOFFERS received. 

are you expecting a wireless connection or wired ? is the router DHCP enabled ? other kit working off the same router ?

---

### Post by CT Husky on 2011-02-11
Thanks to responders. When I ran the commands, I was attempting to connect wirelessly.  However, the laptop also previously had failed to connect when wired over the ethernet cable.

This appears to be solved now. Here is how it got resolved:

I noticed that the live CD I was using was dated, because Update Manager was seeking something like 400 updates.

So, I burned a fresh 10.04.1 LTS CD, presumably updated, then I plugged in the ethernet cable from my router, and restarted the laptop and ran the new live CD.  I used that session to go to Hardware Drivers, and I downloaded the Broadcom STA driver.

I then exited the live CD session, and rebooted the computer, still with the router plugged in.

On reboot, with the Broadcom STA driver presumably on board, the laptop recognized the wired connection.

I then immediately ran update manager, and upon completion I unplugged the wired connection and restarted. Without further ado the laptop for the first time since install saw the wireless networks, I chose mine, and entered the password.

The laptop now seems to connect fine both wired and wireless. I can only assume that whatever ailed it was fixed by one or more of those 400 updates.

One lesson here, I suppose, is to make sure the live CD being used is as current as possible.

Thanks for the responses.

---

### Post by CT Husky on 2011-02-11
P.S.: just in case any other noobs like me are reading this, a couple of clarifications: when I say "I burned a new live CD," I mean I did this with another computer -- not the laptop with connectivity problems.

Second, when I say you should use an updated live CD, I mean when you do the fresh install, not necessarily just for the live CD session.

---

### Post by P4man on 2011-02-11
Installing a driver in a live session does nothing to help the install on to harddisk. Its not persistent, in fact, the root filesystem of a live session is even read only and any changes made to it dont carry over when you install.

What cured it was a working wired connection, and possibly, the fact the firmware for your wifi card was loaded during the live session and is still in the (is that flash memory?) of the wifi card. This *could *mean the card stops working one day if you leave the laptop powered off for too long (for similar reasons, sometimes a wifi card can be made to work by just booting windows, where the windows drivers also (re)loads the wifi firmware).  

It worth checking. run

```
lshw -C network
```

and post the output here. If it says "firmware=N/A " for the wifi card, you might want to fix that, even if it seems to be working fine.

---

### Post by carsonrose on 2011-02-11
my apologies.

---

### Post by CT Husky on 2011-02-17
Yikes, P4man ! That does not sound good.  Tell how I get rid of the "firmware=N/A"

Here is my output for lshw -C network:

ted@ted-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:31:ed:da
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.0.0.5 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:3b:26:9b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)
ted@ted-laptop:~$

---

### Post by P4man on 2011-02-17
That looks okay actually, I think. No firmware is listed for your wired connection, but it doesnt seem like it needs it. Anyhow, I suppose doing this, if you havent already, wont hurt:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20Internet%20access)

---

