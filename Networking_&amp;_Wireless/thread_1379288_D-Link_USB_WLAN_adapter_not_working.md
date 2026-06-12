---
title: "D-Link USB WLAN adapter not working"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by yanvolking on 2010-01-12
Hello Community,

I have just installed Ubuntu 9.10 on an Acer TravelMate 290E.  I've got internet connection through the Ehternet Cable, but when I plug in the D-Link WLAN USB device, although the system recognises it, it is disconnected.  

How can I connect the WLAN USB device adn get it to work?

Thanks

Yan

---

### Post by changingstate on 2010-01-12
I was just doing a little research relating to your other post. 

Would you mind posting the output of :

sudo lshw -C network

lsusb

ifconfig -a

Thanks.

---

### Post by yanvolking on 2010-01-12
Hi Changingstate,

results of the tests you asked for:

yan@yan-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:1a:9e:3f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.101.6 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:10 ioport:c000(size=256) memory:e0002000-e00020ff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:01:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=128
       resources: irq:10 memory:e0000000-e0001fff
  *-network:0
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:0b:6b:4a:e9:5b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Wireless interface
       physical id: 4
       logical name: wlan2
       serial: 00:15:e9:43:14:ea
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
yan@yan-laptop:~$ 


yan@yan-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c040 Logitech, Inc. Corded Tilt-Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07d1:3c03 D-Link System DWL-G122 802.11g Adapter [ralink rt73]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
yan@yan-laptop:~$ 


yan@yan-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:02:3f:1a:9e:3f  
          inet addr:192.168.101.6  Bcast:192.168.101.255  Mask:255.255.255.0
          inet6 addr: fe80::202:3fff:fe1a:9e3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6084 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5462067 (5.4 MB)  TX bytes:538606 (538.6 KB)
          Interrupt:10 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0b:6b:4a:e9:5b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan2     Link encap:Ethernet  HWaddr 00:15:e9:43:14:ea  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0B-6B-4A-E9-5B-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster1  Link encap:UNSPEC  HWaddr 00-15-E9-43-14-EA-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

yan@yan-laptop:~$ 


Bare in mind that my computer has an in-built broadcom WLAN device that does not work in Ubuntu.

Thanks for your efforts

Yan

---

### Post by bkratz on 2010-01-12
It might be be relatively easy to get the internal card working. Have you seen this thread?

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

Just a thought, ignore if you want to.

---

### Post by changingstate on 2010-01-12
You said you were playing with ndiswrapper in the old post, in this post you mention simply that you've installed 9.10. Did you reinstall? ( I'm trying to work out why your system is listing three wireless adapters ... )

Also, could you post results of : 

lsmod | grep rt73usb

lsmod | grep ndiswrapper

just to double check?

---

### Post by yanvolking on 2010-01-13
Hi changingstate,
 
After playing around with my (ACER) computer this morning, I found out that not only does my D-Link USB WLAN device work, but also the internal Broadcom.  The reason I thought none of them was working was that when I clicked on the network applet on the toolbar, I only saw the word "disconnected" under a faded (ie not black) Wireless Networks caption.  But then looking at the available wireless networks on another (DELL) computer I have whose wireless LAN system works, I went to the network connections menue, entered one of the network names found on the DELL in the ISSID box, put in a duff value for the WEP code and presses connect, the wirless applet suddenly responded (a whirling circle) and then below the Wirless Networks caption (now black) appeared the SSID name with a signal strength indicator.  Of course as I dont have the real WEP code I cant connect but at least I know both my WLAN devises are working.

Question : so why can I not see a list of all  the available wireless networks without having to register them one by one by name as above.  In other computers I have with WLAN devices, justy by switching on the computer I can see a list of all available capted WIFI network signals?

Thanks for all your efforts

Yan

---

