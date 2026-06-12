---
title: "Cannot obtain DHCP lease"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by Robert Frittmann on 2010-02-07
Hi, I'm just beginning to learn about Linux networking, so please bear with me. I have a home WiFi network that has been working fine for ages, which currently supports two Windows-based laptops and a WM5 smartphone. They all connect to the WiFi router (Linksys WRT54G) which in turn connects to the ADSL modem (Huawei MT882). The router is configured with a WEP key, the SSID is not being broadcast, and all MAC addresses must be whitelisted. I try to follow good wireless network security practice. I also have NAT running between the router and the modem. 

Everything is working fine for the Windows clients, and now I am trying to add my Linux box to the mix. I am setting up an older HP Pavilion 510a desktop with Ubuntu v8.04LTS, using a Realtek RTL8185 WLAN card. The machine has an onboard RTL8139 LAN adaptor also, which works fine when I plug it in directly to an ethernet port on the wireless router. The WLAN, however, does not seem to be getting a DHCP packet, and keeps on autoconfiguring with a 169.254.x.x address. When I try giving it a static IP address it doesn't connect either.

As you can see from the screenshots below, the WLAN is working fine. I have it installed using the ndiswrapper and Windows drivers. I've been through the [Comprehensive ndiswrapper troubleshooting guide](http://ubuntuforums.org/showthread.php?t=885847) but that did not resolve my problem.

[center][IMG]http://i46.tinypic.com/qqtxty.png[/IMG]

[IMG]http://i48.tinypic.com/2w69aua.png[/IMG][/center]

I configured the network myself, and it works perfectly for my Windows machines. It is just my lack of experience with Linux which is preventing me from getting the wireless to work under Linux. I can get a HDCP packet in Linux when I am connected to the LAN using the RTL8139 adaptor, but not on the WLAN using the RTL8185 adaptor. Any advice would be appreciated.

---

### Post by Azario on 2010-02-07
Try 
sudo dhclient wlan0

---

### Post by Robert Frittmann on 2010-02-07
Thanks **Azario**, here is the outcome of this...

```
myuser@mycomputer:~$ sudo dhclient wlan0
[sudo] password for myuser: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:02:44:?:?:?
Sending on   LPF/wlan0/00:02:44:?:?:?
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
myuser@mycomputer:~$
```

Also just for good measure, here is the output from an ifconfig command...

```
myuser@mycomputer:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:40:2b:?:?:?  
          inet addr:192.168.?.?  Bcast:192.168.?.?  Mask:255.255.255.0
          inet6 addr: fe80::240:?:?:?/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5966 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5241076 (4.9 MB)  TX bytes:1229648 (1.1 MB)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75663 (73.8 KB)  TX bytes:75663 (73.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:02:44:?:?:?  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:f4110400-f4110425 

wlan0:avahi Link encap:Ethernet  HWaddr 00:02:44:?:?:?  
          inet addr:169.254.8.116  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Memory:f4110400-f4110425 

myuser@mycomputer:~$
```

I'm wondering if it has something to do with the two devices listed above, wlan0 and wlan0:avahi.

---

### Post by Robert Frittmann on 2010-02-08
Here is the output of another useful diagnostic tool...
```
myuser@mycomputer:~$ sudo lshw -class network
[sudo] password for myuser: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: eth0
       version: 10
       serial: 00:40:2b:?:?:?
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.10.137 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@0000:01:0d.0
       logical name: wlan0
       version: 20
       serial: 00:02:44:?:?:?
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.52+Realtek,11/18/2004,5.102.11 latency=64 link=no maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11b
myuser@mycomputer:~$
```
I notice from this that there is no such device as *wlan0:avahi* so it would seem to me that the "avahi" device is a shadow of the physical device *wlan0*. Also, I can confirm that the MAC addresses for both the *wlan0* device and the *wlan0:avahi* device are exactly the same. My searching on this issue shows that "avahi" is an implementation of Zero Configuration. That would explain the 169.254.x.x IP address that keeps appearing, even if there is no DHCP scope configured for that range. My questions therefore are:
[list][*]Is this Zeroconf required for normal TCP/IP networking?[*]Can I disable the *wlan0:avahi* device?[*]How do I disable this device?[*]Will this allow the *wlan0* device to receive a DHCP lease?[/list]

---

### Post by Iowan on 2010-02-08
> **Robert Frittmann said:**
> 
[list][*]Is this Zeroconf required for normal TCP/IP networking?[*]Can I disable the *wlan0:avahi* device?[*]How do I disable this device?[*]Will this allow the *wlan0* device to receive a DHCP lease?[/list]Zeroconf is generally not required for normal TCP/IP networking. When it kicks in, it usually indicates a problem getting a "normal" DHCP address. It can be disabled/removed, but ordinarily, the problem lies elsewhere.

---

### Post by Robert Frittmann on 2010-02-08
Thanks **Iowan**, that confirms what I thought was happening. So now I just need to identify the cause of the real problem. I might just try installing a new wireless NIC, in case there is a problem with the Realtek. I have a Ralink RT2500 USB device which might do the trick. I suppose that adding the USB bus into the mix will only confuse things further though. Has anyone had an RT2500 working in Ubuntu Hardy?

I'm trying to do this completely without altering the existing Windows network. The only thing I have needed to do so far was to add the MAC address of the Linux box's network adaptor into my router's whitelist. Sure, it is only my home network, but if this were a live environment, and I was wanting to add a new Linux machine to a pre-existing Windows network with hundreds of clients, I would not have the opportunity to reconfigure the entire network just to get one computer working.

---

### Post by chili555 on 2010-02-08
In a system with Network Manager running, manual configuration and terminal commands almost never work. NM has such a firm grip on networking that you can't hardly do anything unless, of course, you simply remove it.

First, find the NM icon at the top right of the desktop, click it and see if you see networks, including yours. Click connect. You will be prompted for encryption details and, if the Koala is with you, you will connect. Here is a sample of what you will see.

---

### Post by Robert Frittmann on 2010-02-08
Hi **chili555**, I think I'm confusing people a bit here. I use Karmic on my netbook, within a Sun VirtualBox environment, running under Win7. However, the problem described in this thread is on a different machine entirely. The system I'm trying to get the wireless NIC working on is a desktop machine, which is solely running Ubuntu v8.04LTS Hardy Heron. I assume there is no such beast as NM under Hardy, am I correct?

---

### Post by Iowan on 2010-02-08
NM existed under Hardy (8.04) - in fact, the NM (r)evolution really began in Hardy. DHCP worked well - static addresses were more of a pain. This box ran Gutsy until I finally added more RAM and (recently) upgraded.

---

### Post by chili555 on 2010-02-08
> NM existed under Hardy (8.04) - in fact, the NM (r)evolution really began in Hardy.As always, Iowan is quite correct. You can open System -> Administration -> Synaptic and see if it's installed. If it's installed, and I'm 99% sure it is, it has networking firmly in control.

---

