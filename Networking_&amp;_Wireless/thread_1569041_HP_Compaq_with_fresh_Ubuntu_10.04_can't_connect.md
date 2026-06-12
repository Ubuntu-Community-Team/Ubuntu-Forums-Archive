---
title: "HP Compaq with fresh Ubuntu 10.04 can't connect"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by LichTheMan on 2010-09-06
The computer is an HP Presario C700 laptop made by Compaq.
I just installed Ubuntu yesterday, version 10.04.1 desktop i386 for a 32 bit laptop.
Ubuntu works great, and if I plug into the internet directly, I have internet, of course (if I didn't, there'd be a problem lol).
But, while on wireless, I can see my network, and edit the settings, but when I connect, it disconnects because it can't get internet.
I took the MAC address from when I was wired and put it in for the wireless network. That did nothing.
I also tried to (for the ipv4 address) have it set automatically, and set manually, but that didn't work either.

Attached is a screenshot of the config of the internet and a list of commands I've found people doing when debugging internet issues.

---

### Post by LichTheMan on 2010-09-06
Bump.

---

### Post by LichTheMan on 2010-09-06
Bump.

---

### Post by Iowan on 2010-09-06
It's generally considered polite to bump no more than once/day (24 hours). Every two hours seems a bit impatient.

---

### Post by LichTheMan on 2010-09-06
Sorry, I was trying to keep it at least on the first page and not get buried.

---

### Post by LichTheMan on 2010-09-07
Bump.

---

### Post by silverglade00 on 2010-09-07
You want to remove the MAC address that you put in. They are unique to the network interface. This means you told it to connect to your wireless network through the wired port.

---

### Post by LichTheMan on 2010-09-07
Even so, doing that changed nothing.
--Fixed--

---

### Post by silverglade00 on 2010-09-07
Ok, part of the bootup files live in your Ubuntu partition. They got wiped out when you turned it into free space. Don't worry you can get everything back. First thing is to find your plug and leave it plugged in through all of this. You should have a large Windows partition, a small FAT or NTFS partition that Compaq sets up for recovery, and possibly one or two other partitions for swap and Linux (ext3 or 4). Use your Live CD to boot up and run the installer. Ignore the FAT and NTFS partitions and delete the rest. Then you can choose to install in the free space. Once that is done, run your updates and also install the Hardware Drivers. That should get you going.

---

### Post by LichTheMan on 2010-09-07
Alright, ignore the last post.
I need to focus on getting the wireless to work now.
If someone could TeamView me, that'd be great.

---

### Post by LichTheMan on 2010-09-07
Here's some more info if it helps.

```

tyler@TYLER-PC:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:1f:e1:4d:05:80
Sending on   LPF/wlan0/00:1f:e1:4d:05:80
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8

No DHCPOFFERS received.
No working leases in persistent database - sleeping.
sudo ifconfig wlan0
tyler@TYLER-PC:~$ 
tyler@TYLER-PC:~$ sudo ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1f:e1:4d:05:80  
          inet6 addr: fe80::21f:e1ff:fe4d:580/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9814 (9.8 KB)  TX bytes:29940 (29.9 KB)

tyler@TYLER-PC:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"belkin54g"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:17:3F:F1:FE:DA   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-25 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by LichTheMan on 2010-09-07
Fixed.
You can solve it now.

---

### Post by Iowan on 2010-09-07
> **LichTheMan said:**
> Fixed.
You can solve it now.You mean [Mark it Solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?
You can do that, too. :)

---

### Post by LichTheMan on 2010-09-08
Sorry, I'm just used to editing the first thread and changing the prefix.

---

