---
title: "Can connect to router but cannot access interwubs through it :/"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by beleth on 2008-12-27
Trying to fix home wireless network belonging to a relative. The DSL modem is functional in the sense that I can connect to interwubs with an ethernet cord, however the router seems to be configured incorrectly. Though the router is operational and its set-up page is accessable through wifi and lan, there is no internet connectivity through the router when it's wired to the modem. My hypothesis is a local ip conflict of some sort, as reconfiguring the router using the wizard did not solve the problem, however I don't know how to fix that and am open to any suggestions.

Sorry for not having better questions to ask, but I'd be happy to provide any bash output that diagnosis requires :/

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"NETGEAR"  Nickname:"omgwtfbbq?"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:99:1C:FA   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-26 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
$ cat /etc/resolv.conf
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5015
#
### END INFO



nameserver 204.215.43.3
nameserver 209.26.88.31

```

---

### Post by pytheas22 on 2008-12-27
> 
The DSL modem is functional in the sense that I can connect to interwubs with an ethernet cord

Just to clarify: do you mean then that when you connect the Ubuntu machine to the router via ethernet, it works fine and can browse web pages, etc.?  It's only when it's connected via wireless that things don't work?

Please also post the output of these commands to help rule out some things:
```

ping -c 5 204.215.43.3
ping -c 5 google.com
ping -c 5 72.14.205.100
wget google.com
wget 72.14.205.100
ifconfig
netstat -r
lspci -nn
lsusb
```

I know that's a lot of stuff to ask for, but it will be helpful.

---

### Post by hexanol on 2008-12-27
As from what I understand, he's able to access the internet only when his computer connect directly to his modem, but not when there's the router between his computer and the modem.

But yeah, please post
```
ifconfig

```
and
```
netstat -rn
```

---

### Post by beleth on 2008-12-27
> Just to clarify: do you mean then that when you connect the Ubuntu machine to the router via ethernet, it works fine and can browse web pages, etc.? It's only when it's connected via wireless that things don't work?
Yes, that's the situation. Two other laptops running OSX and XP are similarly able to connect to the network but unable to reach the delicious tubes.

This is output while my system is wired to the router.
```
$ ping -c 5 204.215.43.3
PING 204.215.43.3 (204.215.43.3) 56(84) bytes of data.

--- 204.215.43.3 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms

```
```
$ ping -c 5 http://www.google.com
ping: unknown host http://www.google.com

```
```
$ ping -c 5 72.14.205.100
PING 72.14.205.100 (72.14.205.100) 56(84) bytes of data.

--- 72.14.205.100 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms

```
```
$ wget google.com
--19:23:32--  http://google.com/
           => `index.html'
Resolving google.com... failed: Name or service not known.
```
```
$ wget 72.14.205.100
--19:25:35--  http://72.14.205.100/
           => `index.html'
Connecting to 72.14.205.100:80... failed: Connection timed out.

```
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:ea:0e:ee  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:feea:eee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48754 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40734 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51680924 (49.2 MB)  TX bytes:5691685 (5.4 MB)

eth1      Link encap:Ethernet  HWaddr 00:1a:73:47:c0:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9725 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10012 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3601658 (3.4 MB)  TX bytes:1303799 (1.2 MB)
          Interrupt:17 Memory:f0000000-f0004000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:135705 (132.5 KB)  TX bytes:135705 (132.5 KB)

```
```
$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         192.168.0.1     0.0.0.0         UG        0 0          0 eth0

```
```
$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 01)
02:06.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
02:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile [8086:1068] (rev 01)
10:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

```
```
$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by pytheas22 on 2008-12-27
hmmm, based on everything you posted, it looks like everything is working correctly on Ubuntu's end.  Since you say that OS X and Windows have the same exact problem, I strongly suspect that it lies solely with your router, not any of the clients.

Can you access the router's configuration page when connected wirelessly, or only when you're on ethernet?

Have you tried turning the router off for a few minutes and restarting it?  This may well do the trick.

---

### Post by beleth on 2008-12-27
The configuration page is available over ethernet and wifi, and power-cycling hasn't solved the problem anymore than resetting and reconfiguring. Everything seems to be working nicely on the component level, but the network still isn't functioning :/

I know this is a forum dedicated to Ubuntu issues, so do you perhaps know of a place where my query would be more suitable?

---

### Post by pytheas22 on 2008-12-27
> The configuration page is available over ethernet and wifi

But you really can't access any web pages over wifi?  And they really work completely fine over ethernet on all three operating systems?

If that's the case, the only suggestions I can make are to double-check to ensure that you're not disabling web access over wireless for some reason in the configuration, and to contact your ISP (although even this doesn't make too much sense given the fact that connection over ethernet works fine).

Unfortunately I don't know of any forums where you might be able to find better help, but I'm sure that if you google you'll find something.  You could also try contacting the router manufacturer.

---

### Post by beleth on 2008-12-27
> But you really can't access any web pages over wifi? And they really work completely fine over ethernet on all three operating systems?

Not quite, the only way the computers can access the internet is by connecting directly to the modem. Connecting to the router by wifi or ethernet leaves only the configuration page accessable, no internet.

---

### Post by pytheas22 on 2008-12-28
> Not quite, the only way the computers can access the internet is by connecting directly to the modem. Connecting to the router by wifi or ethernet leaves only the configuration page accessable, no internet.

That at least makes a little more sense, although unfortunately I can't think of much you could do besides try to contact the router manufacturer.

You may also want to see if you can upgrade the router firmware.  Most would have an option to find firmware updates automatically over the Internet.  If your router is able to download updates, then you know that its connection to the Internet works (plus maybe the firmware update would solve your problem).

---

