---
title: "netgear wg111v3 seeing router but not web"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by black, one sugar on 2009-05-26
I am trying to get a wireless connection going. The wired connection
working lovely, I have bought a Netgear WG111v3 thinking it would be
Ubuntu friendly.. IN fact I just bought the WG111 without realising
there were versions, as it looked pretty idiot-proof in the reviews of
supported hardware.. I should have looked closer, the v1 and v2 sound
much easier !

Anyway, I am trying to connect to another Netgear device, my SKY router
which I think is a Netgear DG934G. So far I have been blundering about a
bit, trying to follow advice on
[http://ubuntuforums.org/showthread.php?t=732827](http://ubuntuforums.org/showthread.php?t=732827) mostly.

I am running JAUNTY 9.04 clean install on a DELL Inspiron 8200 ( quite old laptop )

I think I am nearly there, the name of the wireless connection is
visible in the top right corner with a bar showing good reception ( and
my neighbour's SKY network too, a good sign I suppose ) .. However when
I try to connect to it, it doesn't seem to like the thing I believe to
be my WPA key. I took the key off the bottom of the router, and I have
verified it by logging into [http://192.168.0.1/router_status.html](http://192.168.0.1/router_status.html) . Its
an eight character long key all UPPERCASE . 

Something that seems odd is after I have saved the key, when i go back
to that page later, its morphed into a 22 character key. This occurs
when I allow application nm-connection-editor to access password for
Network secret if I click for SKY31666/802-11-wireless-security/psk
which is an option I get when I try to connect. Is this a WEP key or
something? Why is it overwriting the one I put in ? Even if I put my WAP
key in, it seems to end up with the other one.

This may all be red herring though !

I can connect to the router on my other laptop, wirelessly, using XP and
a Speedtouch 110g wireless card, I dont really want to change the
settings on the router as that connection will then be mangled. That
connection says its WPA-PSK and has an 8 character key, which is the one
I have been trying to use on the Ubuntu machine.

People with similar problems seem to usually be asked to list outputs of
various commands, so I will list them below, in the hope that it sheds
more light than my rambling .. I am afraid I am not well versed enough to edit the wireless-relevant info out from the other stuff, so I havent listed every command I saw suggested on HOWTO post a Wireless issue (ticket) [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) as it would be reams and reams . Please just yell if you would like me to run any other commands.


Please give me some advice on all this.. I suspect its not got far to go
to get it working, but I am foxed. I am pretty wet behind the ears when
it comes to Ubuntu, only been using it for a month, and I was no techy
before then, so layman's language would be appreciated. thanks.

Below is the output from sudo lshw -C network   (after I unplug the
Ethernet cable )

neil@neil-laptop:~$ sudo lshw -C network
[sudo] password for neil: 
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:08:74:e4:75:bb
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii
10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x
duplex=half ip=192.168.0.2 latency=32 link=yes maxlatency=10 mingnt=10
module=3c59x multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1e:2a:c3:1d:76
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wg111v3
driverversion=1.53+NETGEAR Inc.,04/23/2007,5.1 link=no multicast=yes
wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 6a:64:7d:02:5b:4e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3
firmware=N/A link=yes multicast=yes
neil@neil-laptop:~$ 

BELOW OUTPUT FROM lssub

neil@neil-laptop:~$ lsusb
Bus 002 Device 002: ID 0846:4260 NetGear, Inc. WG111v3 802.11g Adapter
[realtek RTL8187B]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
neil@neil-laptop:~$ 

Below output from lspci

neil@neil-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
neil@neil-laptop:~$ 





Below are my router settings from [http://192.168.0.1/router_status.html](http://192.168.0.1/router_status.html)

          Firmware Version
V2.02.44

             ADSL Port 
            MAC Address
00:1e:2a:21:1f:41 
             IP Address
90.211.81.165
            Network Type
PPPoA
           IP Subnet Mask
255.255.255.255
         Gateway IP Address
87.87.252.95
         Domain Name Server
90.207.238.97
90.207.238.99

             LAN Port 
            MAC Address
00:1e:2a:21:1f:40
             IP Address
192.168.0.1
                DHCP
On
           IP Subnet Mask
255.255.255.0

               Modem 
       ADSL Firmware Version
7.03.01.66
            Modem Status
Connected
    DownStream Connection Speed
9922 kbps
     UpStream Connection Speed
764 kbps
                VPI
0
                VCI
38

           Wireless Port 
            Name (SSID)
SKY31666
               Region
Europe
              Channel
1
            Wireless AP
Enabled
           Broadcast Name
Enabled

---

### Post by superprash2003 on 2009-05-26
post output of
1)ifconfig
2)ping 208.67.222.222

---

### Post by black, one sugar on 2009-05-26
thanks ! I have done these with the ethernet cable out, hope thats right..

neil@neil-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:74:e4:75:bb  
          inet6 addr: fe80::208:74ff:fee4:75bb/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7682 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8580713 (8.5 MB)  TX bytes:873280 (873.2 KB)
          Interrupt:11 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:2a:c3:1d:76  
          inet6 addr: fe80::21e:2aff:fec3:1d76/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3875 (3.8 KB)  TX bytes:3831 (3.8 KB)

neil@neil-laptop:~$ 
neil@neil-laptop:~$ ping 208.67.222.222
connect: Network is unreachable
neil@neil-laptop:~$

---

### Post by superprash2003 on 2009-05-27
your wlan0 isnt getting an ip address. post output of the following commands
1)iwconfig
2)sudo dhclient wlan0

---

### Post by 3rdalbum on 2009-05-27
> **black, one sugar said:**
> 

Something that seems odd is after I have saved the key, when i go back
to that page later, its morphed into a 22 character key. This occurs
when I allow application nm-connection-editor to access password for
Network secret if I click for SKY31666/802-11-wireless-security/psk
which is an option I get when I try to connect. Is this a WEP key or
something? Why is it overwriting the one I put in ? Even if I put my WAP
key in, it seems to end up with the other one.

This may all be red herring though !

Yep, that's a red herring. All encryption algorithms (for wireless encryption, file encryption etc) require the key to have a particular number of characters. If you use a WPA passphrase (which can be any length), it gets converted into a 22 character string by a technique known as "hashing" (see Wikipedia for more details). This is the WPA key. This not only satisfies the encryption algorithm, but it also makes the encrypted traffic more secure - a good thing!

Hashes cannot be "unhashed", and for security Network Manager only stores the hash/key. Therefore, if (for instance) the connection fails and NM asks you for your passphrase or key again, it will show the 22-character key that it tried before, not your passphrase.

---

### Post by black, one sugar on 2009-05-27
iwconfig  gives

neil@neil-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

sudo dhclient wlan0   gives

neil@neil-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:2a:c3:1d:76
Sending on   LPF/wlan0/00:1e:2a:c3:1d:76
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
neil@neil-laptop:~$ 

Thanks for your help, Superprash ..  Afraid I will be a bit intermittent over next few days as have limited access to this PC

---

### Post by superprash2003 on 2009-05-28
just to test , disable wifi security temporarily and see if you can connect to your wifi network then..

---

### Post by black, one sugar on 2009-05-28
phew ! Just tried that and it worked.. 5 Mb/s indeed ! Much quicker than my windows wireless !!!

However I have gone back to the yellow ethernet cable coz a system without any security makes me a bit nervous ...

btw will be off air soon for about 3 days ...

---

### Post by black, one sugar on 2009-05-28
I will be here another day, it rurns out, shorter camping trip but more time for Ubuntu !

So , to me, its looking like the problem lies with the security on the interface between the USB WG
111v3 and the router, as it works lovely with no security.. You think so ?


thanks for your help

---

### Post by black, one sugar on 2009-05-28
Out of curiosity, I now applied the tricks I have learnt to my original Speedtouch PCI wireless card..  and got that to work without wireless scurity too  !

So with either the Speedtouch 110g PCI card or the WG111v3 USB dongle the probkem only manifests when you try to use the WPA-PSK encryption, they both work well with no security.. The Speedtouch is even faster : 8Mb/s  ;-) .. connected thru it at the moment  .. going back to nice safe yellow leaad tho ...

---

### Post by superprash2003 on 2009-05-28
take a look at this [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

