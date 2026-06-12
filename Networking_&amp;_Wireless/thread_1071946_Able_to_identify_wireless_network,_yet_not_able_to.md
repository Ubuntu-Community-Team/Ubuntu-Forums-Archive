---
title: "Able to identify wireless network, yet not able to connect"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by linuxquestusa on 2009-02-16
Upgraded from Gutsy Gibbon to Hardy Heron.

Here is the situation:

1. Have a Linksys WUSB54G v4 that uses a rt2500 usb driver, which is identified with the upgrade to Hardy Heron.

2. Able to see my network, yet not able to connect to it.

3. Typed the following commands and here is the accompanying info:

**_LSPCI_**:
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
02:01.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)


**_IFCONFIG_**:
eth0      Link encap:Ethernet  HWaddr 00:13:d3:ba:a9:99  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xdd00 

wlan0     Link encap:Ethernet  HWaddr 00:18:f8:ad:e2:d9  
          inet6 addr: fe80::218:f8ff:fead:e2d9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


_**IWCONFIG**_:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Belkin_N1_Wireless_3CACF6"  
          Mode:Auto  Frequency:2.432 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


_**CAT /etc/network/interfaces**_:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface


iface wlan0 inet static
address 192.168.1.46
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxx
             
wireless-essid 05B412179091

auto wlan0


address 192.168.1.46
netmask 255.255.255.0
gateway 192.168.1.1



iface eth0 inet dhcp

auto eth0


I'm having a VERY frustrating experience with Hardy Heron and yes I've looked extensively through the Unbuntu forums and am still having the following problem:

Linksys Wireless adapter, model: WUSB54G v4 identifies the surrounding networks along with the one that is appropriately mine, yet it won't allow me to connect.

_Tried the following_: 

Shutdown the down the router and disconnected the Linksys wireless adapter and waited about 20 seconds.

Reconnected the router and wireless adapter and still no Internet connection.

Set everything to DHCP and that hasn't worked either.

Also tried STATIC IP and that didn't work either.  More specifically:

IP ADDRESS: 192.168.1.46
NETMASK: 255.255.255.0
DNS: 192.168.1.1
GATEWAY: 192.168.1.1

What specifically do I need to do other than what I've already done that will allow me to connect to the Internet?

Please advise.

Your help will be greatly appreciated.

Paul

---

### Post by mikewu on 2009-02-17
If nm-applet isn't running already, try starting that. It should automatically configure the wireless connection info.

Otherwise, try manually requesting a connection.

(You can skip this if you already know your network name)
> sudo iwlist wlan0 scan 

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:E5:9E:67:0F
                    ESSID:"linksys"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/100  Signal level=-47 dBm  Noise level=-72 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:tsf=0000008c6094a580

Once you know your essid 

sudo iwconfig wlan0 essid "name of essid"

Command should not return any output

> sudo dhclient 

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/wlan0/00:14:a5:06:ee:a7
Sending on   LPF/wlan0/00:14:a5:06:ee:a7
Listening on LPF/eth0/00:e0:b8:92:5a:13
Sending on   LPF/eth0/00:e0:b8:92:5a:13
Sending on   Socket/fallback
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 3
DHCPREQUEST of 192.168.1.14 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
DHCPACK of 192.168.1.14 from 192.168.1.1
bound to 192.168.1.14 -- renewal in 33397 seconds.

Hopefully that should get you connected.

Good luck!

---

### Post by linuxquestusa on 2009-02-24
Hello Mikewu,


Thank you for getting back to me in a timely manner when you did.

I really appreciate this!

I wanted to send back a response to you that resulted in success and unfortunately it has taken me over week to get this done due to being under the weather.

Went through your instructions and the first couple of times I tried

_sudo dhclient_

I got back something like database persistent, sleeping.

When I got this response I manually configured the Wireless Network from a Static IP address to the following:

_Automatic DHCP_

From here I deleted the WEP key that was listed and Enabled Roaming.

At this point went back to the existing terminal session I had open and typed

_sudo dhclient_

Funny thing, in the top right-hand corner of the computer screen the icon changed from a computer monitor to a series of bars.

Then the Passphrase menu popped-up asking for the Wep key phrase.

When I typed the passphrase the terminal session continued and my computer received a new IP address.

From here I opened my browser and sure enough, the Yahoo web site came up no problem, and I said COOL!!


Would like to know the following:

Should I upgrade to Intrepid IBEX or leave it as Hardy Heron knowing the frustrations I've had with getting Internet connection?

Reason for asking is because I would like to upgrade wireless security to either WPA-PSK or WPA-PSK 2.

What do you advise?

Paul

---

