---
title: "Ubuntu as router: Only fast internet on LAN activity"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by Milenco on 2009-11-10
Today I've configured my laptop running Ubuntu Server 9.10 to function as a router. Everything seems to be working, I got internet running on both my PC and the router (Ubuntu Server 9.10). The only problem is the internet speeds, which are way too slow.

I did some research and was able to pinpoint the problem: When downloading a testfile from the internet (wget on the router) the speed seems to be stable at around 100KB/s. The same happens on my own PC. This is too slow, my internet connection is 35Mbit so I should be able to get downloads up to 4MB/s.

Here's the strange thing: When downloading or uploading internally the internet speed boosts up. So this is what happens:

On the router: I start wget to see a stable speed of 100KB/s
On the PC: I download/upload a file to the router using samba (speeds are normal, about 8-9MB/s)
On the router: During the samba activity, the wget download which is still running goes from 100KB/s stable to 4MB/s stable.

Whenever the samba connection is finished, the wget speed drop to 100KB/s again.

On my PC it's the same. Normally download is about 100KB/s. When starting a local connection to the router (uploading/downloading a testfile using samba) the internet speed increases to about 500KB/s (which is not 4MB/s but that makes sense since I'm also uploading/downloading to the router).

The speed not only increases when using Samba, also when creating a connection from my PC to the router using WinSCP.

I can't seem to figure out the problem.

These are the network cards I'm using: 
eth0 -> Internet -> 06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
eth1 -> LAN -> 07:00.0 Ethernet controller: D-Link System Inc DFE-690TXD CardBus PC Card (rev 10)

My ifconfig output:
```

eth0      Link encap:Ethernet  HWaddr 00:16:d3:42:f0:66
          inet addr:85.113.252.something  Bcast:85.113.255.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:815318 errors:16078 dropped:27036 overruns:15888 frame:0
          TX packets:453071 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1105734870 (1.1 GB)  TX bytes:37910931 (37.9 MB)
          Interrupt:20 Base address:0x3000

eth1      Link encap:Ethernet  HWaddr 00:24:01:60:c3:af
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1229982 errors:459 dropped:856 overruns:459 frame:0
          TX packets:1560083 errors:0 dropped:0 overruns:13 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1118633774 (1.1 GB)  TX bytes:1685840901 (1.6 GB)
          Interrupt:22 Base address:0x3400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1054475 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1054475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:195325109 (195.3 MB)  TX bytes:195325109 (195.3 MB)

```

---

### Post by SlugSlug on 2009-11-10
Is the laptop running in some form of low power mode, and ssh / samba 'wake' the card up a bit..?

---

### Post by Milenco on 2009-11-10
I just checked my BIOS settings and found no power-saving options. Also, /etc/pm only contains a folder sleep.d including 2 files (10_grub-common and action_wpa) to handle resume. So I don't believe the problem lies in powersaving (although I'm not sure where else to look)

---

### Post by Milenco on 2009-11-10
A small update: uploading from the WAN interface seems to be working just fine. When people download files from the apache2 server installed on the router, they get downloadspeeds around 4MB/s, which is my top uploadspeed.

---

### Post by Milenco on 2009-11-10
Ok I did some more testing and here are my findings:

-Both ethernet adapter seem to be working just fine. When I connect them both to my LAN I get throughput speeds around 10.5MB/s.
-Uploading from the WAN (eth0) interface always works as it should be, whether or not I'm uploading from the LAN to the router.
-When wgetting a file after a fresh boot, speeds are normal (3-4MB/s) for just a few seconds, then the speed drops to 100-150KB/s.
-When wgetting a file, speeds are about 100KB, until I start to upload from my desktop to the Ubuntu Server (LAN side). When upload starts, the wget speed increases to 3-4MB/s. 
-When wgetting two files simultaneously, both wget's seem to benefit: From 1x100KB/s connection it goes to 2x300~KB/s.
-This is also the case on my desktop, which is connected to the Ubuntu Server 9.10 router: 
--FTP downloads won't get above 100KB/s.
--However, when I use torrent to get a file (with about 100 seeders), the downloads hit my connection limit: 4.2MB/s

This Ubuntu server is a fresh install (I installed it last week), with LAMP running, ddclient, dhcp3-server, dns, proftpd and samba. 

This is without a doubt the weirdest problem I've come across in my entire IT-life. I don't have a clue where to look. Any help would be greatly appreciated!

---

### Post by Milenco on 2009-11-11
Anyone?

---

