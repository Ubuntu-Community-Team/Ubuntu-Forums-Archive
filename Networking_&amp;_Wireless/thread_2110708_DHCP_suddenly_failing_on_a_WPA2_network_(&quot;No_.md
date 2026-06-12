---
title: "DHCP suddenly failing on a WPA2 network (&quot;No DHCPOFFERS received&quot;)"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by soulspit on 2013-01-30
Hi everyone.

I have always been able to connect to my WPA2 personal protected wifi network with the Network Manager. A couple days ago, this stopped working - I also tried Wicd and that did not work. Other machines (including my laptop when I boot into Windows) can connect to this network. Also, I can connect to it when I disable the wifi security, or connect via wired connection.

I have tried connecting purely from the command-line with wpa_supplicant - it appears to connect to the network, but DHCP fails. This is what I tried:

```
$ sudo stop network-manager
$ sudo ifconfig eth1 down
$ sudo dhclient -r eth1
$ sudo ifconfig eth1 up
$ wpa_passphrase [my ssid] [passphrase] > /home/tut/wpa.conf
$ sudo wpa_supplicant -Dnl80211 -ieth1 -c/home/tut/wpa.conf # i have also tried the wext driver
Trying to associate with c0:c1:c0:cd:21:5f (SSID='headsoak' freq=2412 MHz)
Associated with c0:c1:c0:cd:21:5f
WPA: Key negotiation completed with c0:c1:c0:cd:21:5f [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to c0:c1:c0:cd:21:5f completed (auth) [id=0 id_str=]
```

Then, in a separate console:

```
$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 08:ed:b9:4d:60:b9  
          inet6 addr: fe80::aed:b9ff:fe4d:60b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4557 errors:6 dropped:0 overruns:0 frame:68187
          TX packets:5514 errors:320 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2662098 (2.6 MB)  TX bytes:1894124 (1.8 MB)
          Interrupt:17
$ iwconfig eth1
eth1      IEEE 802.11abg  ESSID:"headsoak"                                                                                    
          Mode:Managed  Frequency:2.412 GHz  Access Point: C0:C1:C0:CD:21:5F                                                  
          Retry  long limit:7   RTS thr:off   Fragment thr:off                                                                
          Power Management:off

$ sudo dhclient -v eth1
Internet Systems Consortium DHCP Client 4.1-ESV-R4
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/08:ed:b9:4d:60:b9
Sending on   LPF/eth1/08:ed:b9:4d:60:b9
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
[a couple dozen more of these]
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
DHCP connection failed
```

No luck! Here is the output of **ifconfig** (while connected via ethernet), **lspci**, and **lshw**, and also **/etc/network/interfaces**:

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr ac:16:2d:4b:3c:90  
          inet addr:192.168.1.121  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ae16:2dff:fe4b:3c90/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1633 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1379 errors:0 dropped:166 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1295327 (1.2 MB)  TX bytes:287284 (287.2 KB)
          Interrupt:43 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 08:ed:b9:4d:60:b9  
          inet6 addr: fe80::aed:b9ff:fe4d:60b9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4561 errors:11 dropped:0 overruns:0 frame:102163
          TX packets:5549 errors:405 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2662706 (2.6 MB)  TX bytes:1904594 (1.9 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9703 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9703 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:818601 (818.6 KB)  TX bytes:818601 (818.6 KB)

$ lspci -vv | grep Network
08:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:07:00.2
       logical name: eth0
       version: 0a
       serial: ac:16:2d:4b:3c:90
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.121 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:c1404000-c1404fff memory:c1400000-c1403fff
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: 08:ed:b9:4d:60:b9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:c1500000-c1503fff

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

My laptop is an HP Envy 4t Sleekbook. I'm running Kubuntu 12.04, kernel 3.2.0-35.

Any thoughts would be greatly appreciated! Let me know if I can send any more output your way.

---

### Post by SeijiSensei on 2013-01-31
I've seen reports here of problems with Broadcom wireless devices after recent updates.  I'd start by reading those.

---

### Post by soulspit on 2013-01-31
Thanks for the tip! It started me off on a goosechase with various solutions, none of which worked directly. I did, however, get it to work. For posterity and googling, I'll try to detail what I figured out.

Most suggestions involved setting up the b43 wireless driver (for instance installing/reinstalling bcmwl*, b43-fwcutter, etc., then modprobe b43 or modprobe wl). *I don't think these work well (or at all) for the BCM4313 wireless card*.

In the end, after installing and then purging various packages related to b43, it suddenly started working. Having done the following at some point probably helped:

```
sudo apt-get update
sudo apt-get install linux linux-headers-generic kernel-package
sudo update-burg # i use burg instead of grub, and i think it didn't update automatically
```

In Additional Drivers, the Broadcom STA drivers are *not* activated. The wireless drivers/modules that work for me are brcmsmac and bcma, and these ended up selected automatically:
```
$ lsmod | grep bcma
bcma                   26696  0 
$ lsmod | grep brcmsmac
brcmsmac              570930  0 
mac80211              506862  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205774  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12574  1 brcmsmac

```

[These drivers *do* support the BCM4313]("http://linuxwireless.org/en/users/Drivers/brcm80211").

My guess is that what fixed things for me was simply updating to the latest kernel, which chose the correct drivers automatically and it all worked. Marking as solved.

---

### Post by soulspit on 2013-02-01
For any googlers that land here, the advice I gave in my previous post is not so good. Despite lots of positive results out there for using the bcm/brcmsmac drivers (or just brcmsmac with bcm blacklisted) with the BCM4313 card, it didn't really work for me. It sort of worked but the signal was of such low strength that it was practically unusable.

But I also couldn't get the wl driver from bcmwl-kernel-source to work either.

Instead, I compiled and installed the proprietary Broadcom driver from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) - this is a different version of the wl module from that installed by bcmwl-kernel-source. I followed the readme on that site as well as this post: [http://ubuntuforums.org/showpost.php?p=11582351&postcount=6](http://ubuntuforums.org/showpost.php?p=11582351&postcount=6). When compiling the driver I also needed to apply the patch detailed here: [http://www.linuxquestions.org/questions/slackware-14/compiling-broadcom-driver-947294/#post4689850](http://www.linuxquestions.org/questions/slackware-14/compiling-broadcom-driver-947294/#post4689850) (basically, once you've extracted the driver, edit src/wl/sys/wl_linux.c and replace the line ".ndo_set_multicast_list = wl_set_multicast_list," with ".ndo_set_rx_mode = wl_set_multicast_list,").

And it now works!

One little thing to look out for, if you're using Wicd, is that some drivers (like the brcmsmac) name your wireless as wlan0, and some (like wl) name it as eth1. In Wicd preferences you can set which interface is used for wireless - you might need to check it and switch it to the appropriate interface (which you can see with ifconfig/iwconfig).

Good luck...

---

### Post by ubfan1 on 2013-02-01
You might also try turning off IPV6.  network-manager has a setting for ipv6 which may be set to "ignore", not sure about wicd.

---

