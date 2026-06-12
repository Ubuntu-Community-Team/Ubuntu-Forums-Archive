---
title: "Great connection but no internet in 10.10"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by spatiegames on 2010-11-02
Hi,

The day Ubuntu released 10.10 Maverick Meerkat I upgraded my pc. Everything went fine, until I got to internet. I connected to my wireless network (which is secured with a WEP-key and a MAC-filter). It connected perfectly, 80-90% connection. When I tried opening a webpage it just said loading and nothing happened. This was also the case with updating and installing software.
The funny thing was that I **was** able to use the internet of my phone. I have an HTC Hero, on which I can connect to my wifi-network and share the network through usb-cable. The internet worked fine then but that's not what I have a wifi-card for..
I really needed a computer with a fast internet connection so I downloaded Ubuntu 10.04 through a 9.10 Live CD, burned it and installed it. (Didn't want to lose my files/music so I left the 10.10 partition there and used a migration assistant to get my 10.10 settings, which caused the grub of 10.10 to be left installed. After removing 10.10 I couldn't get into my system anymore :P After some trouble and research I got to reinstall grub and everything works fine now. Don't know if this is relevant but I thought it might be handy to know..)
I thought that the cause of my internet problem might've been upgrading. So I burned the 10.10 desktop ISO to a disk and booted into the Live desktop and connected to my network. Again, it connected perfectly, but the internet did not work at all.

I don't know if I'm the only person with this problem, at least I couldn't find anything on google about this so..

Hopefully someone can help me solve this problem because I really digg the look of ubuntu 10.10.

Might be important::
```
$lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI
02:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
bas@bas-desktop:~$ lspci | grep net
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
bas@bas-desktop:~$ lspci | grep network
bas@bas-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI
02:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)

```

SO: [B]01:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI

[/B]Thanks in advantage,
Spatiegames.

---

### Post by klemes on 2010-11-02
I know it sounds silly but since you employ MAC filtering in your wireless network have you made sure that you have specified correctly the _***wireless MAC address***_ of your desktop in the relevant page of your router's web interface?
Also make sure you are not using any system-wide used proxy servers.
It would help if you posted your /etc/network/interfaces and your /etc/resolv.conf files along with the output of the
following basic commands:
```
 
sudo ifconfig && sudo iwconfig && sudo route

``` 
                                              Cheers,
                                               Klemes.

---

### Post by spatiegames on 2010-11-02
> **klemes said:**
> I know it sounds silly but since you employ MAC filtering in your wireless network have you made sure that you have specified correctly the _***wireless MAC address***_ of your desktop in the relevant page of your router's web interface?
Also make sure you are not using any system-wide used proxy servers.
It would help if you posted your /etc/network/interfaces and your /etc/resolv.conf files along with the output of the
following basic commands:
```
 
sudo ifconfig && sudo iwconfig && sudo route

```                                              Cheers,
                                               Klemes.

The MAC address is definitely filled in correctly as it doesn't change during an installation or an upgrade and my internet works perfectly right now. Also if my MAC address wasn't correctly specified I wouldn't even be able to connect to the network.

I suppose I have to get the files and output from the 10.10 version, and I guess getting 'em from a live run should do it. (If not, please tell me so :P)
I'll post the results in a bit.

---

### Post by spatiegames on 2010-11-02
Ok, here are the results:

/etc/network/interfaces:
```
auto lo
iface lo inet loopback

```

/etc/resolv.conf:
```
# Generated by NetworkManager
domain lokaal
search lokaal
nameserver 192.168.1.254
```

Terminal output:
```
ubuntu@ubuntu:~$ sudo ifconfig && sudo iwconfig && sudo route
eth0      Link encap:Ethernet  HWaddr 00:1a:a0:5a:16:d8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4496 (4.4 KB)  TX bytes:4496 (4.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:a8:15:6a  
          inet addr:192.168.1.41  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:e5ff:fea8:156a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15559 (15.5 KB)  TX bytes:12779 (12.7 KB)

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Pantagruel"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:13:49:16:D7:F6   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:72EA-E011-F5
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
```

Hope this helps to find the problem..

---

### Post by grahammechanical on 2010-11-02
From the listing that you gave wlan0 (the wireless metwork card in your computer) is UP and what is more it is RUNNING. It is connecting to your modem/router. This is the Access Point. The numbers and letters that follow might be the MAC address of the modem/router. The thing is also transmitting (Tx) and receiving (Rx) with no errors. So, why can you not access web pages? Do you have a firewall? There is one inside the router/modem. Ubuntu loads one as Well. It is called UFW. Are these blocking access? I wonder.

Regards

---

### Post by grahammechanical on 2010-11-02
There is a Wireless Trouble Shooting Guide. It says this:

> If you are connected to your router and have an IP address assigned  to your wireless device but can't search the web, you will need to check  to see if you have a DNS nameserver set

Is your wireless connection set for Automatic DCHP? It is listed under IPv4 tab in Edit connections. As regards IPv6, things might work better if you set the method to Ignore.

Regards.

---

### Post by spatiegames on 2010-11-03
> **grahammechanical said:**
> From the listing that you gave wlan0 (the wireless metwork card in your computer) is UP and what is more it is RUNNING. It is connecting to your modem/router. This is the Access Point. The numbers and letters that follow might be the MAC address of the modem/router. The thing is also transmitting (Tx) and receiving (Rx) with no errors. So, why can you not access web pages? Do you have a firewall? There is one inside the router/modem. Ubuntu loads one as Well. It is called UFW. Are these blocking access? I wonder.

Regards

I'm not sure but I do believe I have a firewall in the router/modem.. My dad will never switch off that firewall so I guess I'll have to switch of the UFW?

About blocking IPv6, already tried that, doesn't change things..

---

### Post by Peter09 on 2010-11-03
In a terminal try 
 
```
ping 192.168.1.254
```
 
and 
 
```
ping [www.google.com]("http://www.google.com")
```
 
and post the results.
 
If you get a response from 1) you can get to the router/gateway.
 
If you get a response from 2) you can get to the router + a DNS server + google.
 
Which means its a config issue with your machine.

---

### Post by 3rdalbum on 2010-11-03
Try this set of directions:

[http://www.chrislees.info/ubuntu/opendns.shtml](http://www.chrislees.info/ubuntu/opendns.shtml)

It shows you how to set a different DNS address, in case this is the problem. You can use OpenDNS as a temporary measure until you can find out your ISP's DNS address, or you can use it 24/7.

---

### Post by spatiegames on 2010-11-03
> **Peter09 said:**
> In a terminal try 
 
```
ping 192.168.1.254
```and 
 
```
ping [www.google.com]("http://www.google.com")
```and post the results.
 
If you get a response from 1) you can get to the router/gateway.
 
If you get a response from 2) you can get to the router + a DNS server + google.
 
Which means its a config issue with your machine.

I did that, forgot to copy the results.. The ping to the ip-address went perfectly, though it just kept going on which I don't understand (only used ping on Windows years ago, and that one stopped after like 5 packages..).
Also pinged google, which did give results but not quicker than 20 ms and a lot of packages were missing..

[QUOTE=3rdalbum] 	 		**Re: Great connection but no internet in 10.10**
 		Try this set of directions:

[http://www.chrislees.info/ubuntu/opendns.shtml](http://www.chrislees.info/ubuntu/opendns.shtml)

It shows you how to set a different DNS address, in case this is the  problem. You can use OpenDNS as a temporary measure until you can find  out your ISP's DNS address, or you can use it 24/7. 	[/QUOTE]
Tried that too, no change...

---

### Post by Peter09 on 2010-11-03
As a sanity check, go to as near the wireless router as possible (to give you a strong signal) and try to browse the web. 
 
I am concerned when you say there were a lot of packets missing - sounds like some sort of poor connection.
 
The fact that you can ping google by name means that you can get to a DNS server and that you have some sort of connection.

---

### Post by spatiegames on 2010-11-03
> **Peter09 said:**
> As a sanity check, go to as near the wireless router as possible (to give you a strong signal) and try to browse the web. 
 
I am concerned when you say there were a lot of packets missing - sounds like some sort of poor connection.
 
The fact that you can ping google by name means that you can get to a DNS server and that you have some sort of connection.

Well, I would have to do that if my internet didn't work perfectly in my Ubuntu 10.04.1 installation (please read my first post first...)

---

### Post by spatiegames on 2010-11-03
*Bump*

---

### Post by Peter09 on 2010-11-04
Does this thread help
 
[http://www1.ubuntuforums.org/showthread.php?t=1574114&page=2](http://www1.ubuntuforums.org/showthread.php?t=1574114&page=2)

---

### Post by spatiegames on 2010-11-04
> **Peter09 said:**
> Does this thread help
 
[http://www1.ubuntuforums.org/showthread.php?t=1574114&page=2](http://www1.ubuntuforums.org/showthread.php?t=1574114&page=2)

It would if there was a solution there..

---

### Post by Peter09 on 2010-11-04
Thought the command
 
```
sudo modprobe rt61pci nohwcrypt=1
```
 
from the thread may be worth a try.

---

### Post by spatiegames on 2010-11-04
> **Peter09 said:**
> Thought the command
 
```
sudo modprobe rt61pci nohwcrypt=1
```from the thread may be worth a try.

Okay, I'll try it later tonight.

---

