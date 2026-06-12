---
title: "WIFI card, can scan, cant connect"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by sean12345 on 2006-07-04
Hi,

My wireless card is recognised and I can scan with iwlist, I just can't connect.  I had this card working under Breezy with wep and ndiswrapper but it was a terrible connection and I had to configure it manually every time.

Here is the code of lshw with just the network devices.
```

sean@laptop:~$ sudo lshw -C network
  *-network
       description: Realtek
       physical id: 0
       version: Rtl8180
       slot: Socket 0
       resources: irq:11
  *-network
       description: Ethernet interface
       product: 3c556B CardBus [Tornado]
       vendor: 3Com Corporation
       physical id: 3
       bus info: pci@00:03.0
       logical name: eth0
       version: 20
       serial: 00:01:03:84:fa:e5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=3c59x driverversion=LK1.1.19 duplex=full ip=192.168.1.101 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:1800-18ff iomemory:e8101400-e810147f iomemory:e8101000-e810107f irq:11
  *-network
       description: Wireless interface
       product: Wireless PCMCIA Card - F5D6020
       vendor: Belkin
       physical id: 1
       bus info: pci@02:00.0
       logical name: wlan0
       version: 20
       serial: 00:30:bd:4c:f9:0a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 multicast=yes wireless=802.11b
       resources: ioport:1400-14ff iomemory:22000000-220001ff irq:11

```

when I scan the network I get this.
```

sean@laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:42:A6:E3
                    ESSID:"Wireless Network 3"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:175  Signal level:0  Noise level:1
                    Extra: Last beacon: 1333ms ago

sit0      Interface doesn't support scanning.

```

If I deactivate my ethernet and wifi card, then try to activate my wifi card.

```

sean@laptop:~$ sudo ifdown eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:01:03:84:fa:e5
Sending on   LPF/eth0/00:01:03:84:fa:e5
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

sean@laptop:~$ sudo ifdown wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:30:bd:4c:f9:0a
Sending on   LPF/wlan0/00:30:bd:4c:f9:0a
Sending on   Socket/fallback
sean@laptop:~$ sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:30:bd:4c:f9:0a
Sending on   LPF/wlan0/00:30:bd:4c:f9:0a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

When I activate my ethernet, It works fine with 255.255.255.255 on port 67
```

sean@laptop:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:01:03:84:fa:e5
Sending on   LPF/eth0/00:01:03:84:fa:e5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 40317 seconds.

```

I have the correct wep key in my network manager, and It used to work with wep, so I see no reason why it doesn't work now.  When I was using ndiswrapper, I used the rtl8180 driver, the same driver listed here and it worked.

Please help.

Thanks.

---

### Post by atrus123 on 2006-07-06
Ok, now I had a problem similar to yours.  You may or may not want to try my solution, as it can be a little messy.

Here's my situation.

I've been a Gentoo person for a long while, and I decided to jump over to Ubuntu to play with 6.06.  In Gentoo, I spent a while finding a wireless program that I could use and use well, and I started with wpa_supplicant, which worked for a few access points, but I could never get it to connect to everything.  Once I moved to wireless tools, I never had another problem (and so few networks use WPA that I just don't need the support).

So the other day I was in a cafe with a hotspot, and I was trying to connect to the wifi with my new 6.06 install, and it just wouldn't connect.  I could see the access point, but I couldn't connect (whether using wpa_supplicant or iwconfig or the Ubuntu gui).  

This is what I did.

# sudo apt-get remove wpasupplicant.
-I'm no Ubuntu guru, but I noticed that 6.06 ships with both wireless tools and wpa_supplicant.  I'm sure there is some perfectly logical reason for this, but I've had problems with wpa_supplicant before, and so I killed it.
This will kill a couple of other Ubuntu related packages as well.  

Now, for ndiswrapper users, for some reason, killing wpasupplicant dropped ndiswrapper from boot up as well, forcing me to modprobe it before I wanted to use wireless.  You can work around this by adding ndiswrapper to /etc/modules

Now my wireless card connects everywhere.

Maybe this will solve your problem as well.

---

### Post by insyzygy on 2006-07-08
It seems you have a belkin F5D6020 card. There is a known bug regarding this card and the 2.6.15 kernel which dapper uses. It is described here,
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34752]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34752")
I have one of these cards and had the same problem (could scan but not connect). I was able to get it to work but it wasn't pretty. As described in the bug report people have been able to get it to work by custom compiling newer kernels. Based on this last weekend I custom compiled a 2.6.17 (most recent) kernel, and used the firmware from edgy (the next ubuntu version which is in development and is based on the 2.6.17 kernel). After that the belkin card worked fine. However, its probably not worth the hassle unless your into compiling your own kernels. Personally it gave me an excuse to learn how to do it as I had never had a reason to before. You might want to just buy another card. 

Also I tried ndiswrapper but couldn't find windows drivers that worked with it. 

If you want more info on the custom kernel let me know.

---

### Post by sean12345 on 2006-07-12
I would love more information on the custom Kernal. I compliled my own 2.6.17 kernal, but I used "make oldconfig" to speed up the process and I didn't include ndiswrapper as a module.  Hence it didnt work. 

I would rather recompile another kernal than get another card, just for the learning factor.

Thanks
Sean

---

### Post by timmahhny on 2006-07-12
> I would love more information on the custom Kernal. I compliled my own 2.6.17 kernal, but I used "make oldconfig" to speed up the process and I didn't include ndiswrapper as a module. Hence it didnt work.

I would rather recompile another kernal than get another card, just for the learning factor.

Thanks
Sean

If you get it to work, let me know how you did it. I also have an F5D6020 ver 2 card and seem to can't get that to work. I also have a Linksys Wireless G card that a person from a local group here just helped me get it to work. Still having problems with connecting but I am going to try out what that other person said.
Timmahhny

---

### Post by insyzygy on 2006-07-13
If you compiled a 2.6.17 kernel you probably don't have to recompile. Oldconfig should have used the standard ubuntu options which would include support for the belkin card (atmel chipset). If your not sure look in /lib/modules/<2.6.17 kernel name>/kernel/drivers/net/wireless/ 
are there modules named atmel.ko and atmel_cs, if they are there your fine.


Your probably just missing the new firmware. The same that thing that happened to me I compiled 2.6.17.3 from kernel.org and it still didn't work, then I found out I needed newer firmware. So I downloaded the development ubuntu kernel using the git instructions on this page 

[https://wiki.ubuntu.com/KernelGitGuide]("https://wiki.ubuntu.com/KernelGitGuide")

If you look on your computer you have a directory /lib/firmware/<kernel version>. If you installed a vanilla kernel you probably don't have any firmware for your 2.6.17 kernel. Create a directory /lib/firmware/<2.6.17 kernel name>

(the 2.6.17 kernel name is whatever uname -r returns while your running that kernel version.)

Then copy the new firmware located in /ubuntu-2.6/debian/firmware to /lib/firwmare/<my 2.6.17 kernel name>/

```
 cp /ubuntu-2.6/debian/firmware/*/*.* /lib/firmware/<2.6.17 kernel name>
```
and then the belkin card just worked.

---

