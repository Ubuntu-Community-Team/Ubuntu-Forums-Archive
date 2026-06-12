---
title: "no internet connection via cable modem (newb)"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by Kelderkeuken on 2006-07-04
Hello all, this is my first post. I'm really looking forward to making the switch away from Windows, but right after the first install of Ubuntu 6.06 on a clean system I've ran into a problem. I don't know much about networks and even less about unix/linux, I hope someone can glance over this information and spot what is wrong.

I use a *Motorola "Surfboard" SB5100E* cable modem. The ISP requires a certain computername for identification, in my case *cp36986-a*. In windows 2k/xp, setting this computername is enough to set up the connection, i do not have to enter a domain or anything. I'm currently posting this on win 2k that I've installed on one of the fat32 drives (temporarily I hope) so I don't think it can be serverside.

In Ubuntu, the eternet card is recognized and it says it's enabled in the networking settings. It's also set to 'dhcp'. But I can't seem to open a page in firefox. I've searched and browsed these forums and other pages to find a solution, but my understanding of both networking and unix/linux is too bad to really grasp what solutions are applicable to my situation. 

I'm going to post the responses to the following commands:[LIST][*]ifconfig -a
[*]lspci
[*]lsusb *(modem is not connected by usb)*
[*]route -n *(empty?)*
[*]cat /etc/network/interfaces
[*]sudo /etc/init.d/networking restart[/LIST]If you want to have a look but need more/other information, please let me know! *Thanks a bunch in advance!*

Kasper.

```
**kasper@cp36986-a:~$ ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:20:ED:33:67:9A
          inet6 addr: fe80::220:edff:fe33:679a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:672 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:42302 (41.3 KiB)  TX bytes:1836 (1.7 KiB)
          Interrupt:193 Base address:0x6f00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1456 (1.4 KiB)  TX bytes:1456 (1.4 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

**kasper@cp36986-a:~$ lspci**
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
0000:00:08.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 04)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Mast er IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (reva2)

**kasper@cp36986-a:~$ lsusb**
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 10d6:1100 Actions Semiconductor Co., Ltd MPMan MP-Ki 128 MP3 Player/Recorder
Bus 001 Device 002: ID 046d:c50b Logitech, Inc. Cordless Desktop Optical
Bus 001 Device 001: ID 0000:0000

**kasper@cp36986-a:~$ route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

**kasper@cp36986-a:~$ cat /etc/network/interfaces**
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface dsl-provider inet ppp
provider dsl-provider

**kasper@cp36986-a:~$ sudo /etc/init.d/networking restart**
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:20:ed:33:67:9a
Sending on   LPF/eth0/00:20:ed:33:67:9a
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:20:ed:33:67:9a
Sending on   LPF/eth0/00:20:ed:33:67:9a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by pattere on 2006-07-05
I am running into the same issue.  I'm pretty sure it's a matter of setting up a PPPOE connection, but I have not figured out how to do so for my cable modem.  The only settings I have found are for a for the old phone line modem.  Any advice from other users will be most appreciated.  Thanks.

---

### Post by Kelderkeuken on 2006-07-12
I have managed to get the internet connection working, but only when using a static IP. I can't get Ubuntu to work out its differences with my ISP's dhcp server - do I have to enter the dhcp server somewhere?

In any case, for other people running into this, in windows do Run > "cmd" > "ipconfig /all" and note the ip, subnet mask, gateway and your dns ip's. Enter those in the network settings of Ubuntu after deactivating the ethernet card and switching from dhcp to static ip. Then when you activate your ethernet card again you should be online. Upside is that you bypass the dhcp-server, so you can be online if that server is down. But the downside is that if your isp assigns you a new ip, it doesn't get picked up automatically so that can cause problems. Luckily mine hardly ever seems to do that.

If anyone knows a way to determine why the dhcp connection can't be established I'd appreciate it. But for now I'll consider this issue resolved.

---

### Post by mips on 2006-07-12
My standard response follows:

What hardware are you using, modem/router model etc ???
How is the above hardware configured ???

Try this first:
[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.

---

