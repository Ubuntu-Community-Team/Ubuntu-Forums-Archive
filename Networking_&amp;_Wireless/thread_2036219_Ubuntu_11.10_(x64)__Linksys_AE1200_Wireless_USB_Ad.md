---
title: "Ubuntu 11.10 (x64) / Linksys AE1200 Wireless USB Adapter"
date: 2012-08-01
forum: Networking &amp; Wireless
---

### Post by Jwpe on 2012-08-01
Hi there,

I've been trying to set up my new PC to access my wireless network using a Linksys AE1200 Wireless USB Adapter. Unfortunately, Cisco don't appear to provide drivers for the device for Ubuntu, so I followed the advice in [this thread]("http://ubuntuforums.org/showthread.php?t=1805830") to get the device set up.

Thanks to the comprehensive explanations given in that thread, I'm now connected to my network. However, I'm having issues when it comes to actually connecting to the internet. I cannot reach any pages in-browser, nor can I successfully ping google from terminal.

As requested, here are the results of:

iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"{name of my network}"
          Mode: Managed  Frequency:2.412 GHz  Access Point: {my router's MAC address}
          Bit Rate = 5.5 Mb/s  Tx-Power:32 dBm
          RTS thr: 2347 B  Fragment thr: 2346 B
          Power Management:off
          Link Quality:31/100  Signal level:-76 dBm  Noise level: -96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:172  Invalid misc:299096  Missed beacon:0

```

ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 10:bf:48:83:bd:6f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:264820 (264.8 KB)  TX bytes:264820 (264.8 KB)

wlan0     Link encap:Ethernet  HWaddr c0:c1:c0:68:10:a7  
          inet addr:192.168.0.18  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::c2c1:c0ff:fe68:10a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4487 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1722 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3029890 (3.0 MB)  TX bytes:163627 (163.6 KB)


```

pinging an external and internal IP:

```

ping -c3 74.125.131.99
PING 74.125.131.99 (74.125.131.99) 56(84) bytes of data.
From 192.168.0.18 icmp_seq=1 Destination Host Unreachable
From 192.168.0.18 icmp_seq=2 Destination Host Unreachable
From 192.168.0.18 icmp_seq=3 Destination Host Unreachable

--- 74.125.131.99 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2014ms
pipe 3

ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.0.18 icmp_seq=1 Destination Host Unreachable
From 192.168.0.18 icmp_seq=2 Destination Host Unreachable
From 192.168.0.18 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2015ms
pipe 3

```

It appears that packets simply aren't getting back to me, even from the network itself. Any input would be much appreciated.

---

### Post by chili555 on 2012-08-01
> ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.[COLOR="Red"]0[/COLOR].18 icmp_seq=1 Destination Host UnreachableI feel confident your router is 192.168.0.1:```
ping -c3 192.168.0.1
```I am also quite confident this is 90% or more of your problem:> wlan0     IEEE 802.11g  ESSID:"{name of my network}"
          Mode: Managed  Frequency:2.412 GHz  Access Point: {my router's MAC address}
          Bit Rate = 5.5 Mb/s  Tx-Power:32 dBm
          RTS thr: 2347 B  Fragment thr: 2346 B
          Power Management:off
          [COLOR="Red"]Link Quality:31/100[/COLOR]  Signal level:-76 dBm  Noise level: -96 dBmHow far from the router are you??

---

### Post by noblesse on 2013-04-27
Good day and sorry for intruding on your thread but i saw your conversation on the tutorial thread and i decided to follow you. My problem is similar to his but here is what i got

iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:144 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




ifconfig
eth0      Link encap:Ethernet  HWaddr b8:ac:6f:af:84:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:544 errors:0 dropped:0 overruns:0 frame:0
          TX packets:544 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44720 (44.7 KB)  TX bytes:44720 (44.7 KB)


wlan0     Link encap:Ethernet  HWaddr c0:c1:c0:5e:57:95  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)






~$ ping -c3 198.168.1.1
connect: Network is unreachable




The Kernel IP routing table had




Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


but there was nothing under them.

---

### Post by chili555 on 2013-04-27
Does it scan?```
sudo iwlist wlan0 scan
```

---

### Post by noblesse on 2013-04-27
Thank you for the reply. Here's what it shows

No command 'Sudo' found, did you mean:
 Command 'sudo' from package 'sudo-ldap' (universe)
 Command 'sudo' from package 'sudo' (main)
 Command 'udo' from package 'udo' (universe)
Sudo: command not found

---

### Post by chili555 on 2013-04-27
Not [SIZE=5]S[/SIZE]udo but sudo.

---

### Post by noblesse on 2013-04-27
i didn't know capitalizing could make a difference
interface does not support scanning.

---

### Post by noblesse on 2013-04-27
Update, i was able to see my wirless adapter after i disabled the firewall with

sudo ufw disable

but the power was mistakenly taken out from the socket and its not working after i tried doing that step again.

---

### Post by chili555 on 2013-04-28
Let's check a few more things:```
dmesg | grep -e ndis -e wlan
rfkill list all
```> i didn't know capitalizing could make a differenceAlways; and spelling and all that stuff our teachers whined about. Who knew my 5th grade teacher was a Linux nerd!?

---

### Post by noblesse on 2013-04-28
> **chili555 said:**
> Let's check a few more things:```
dmesg | grep -e ndis -e wlan
rfkill list all
```Always; and spelling and all that stuff our teachers whined about. Who knew my 5th grade teacher was a Linux nerd!?

Here's what it showed.

noblesse@PC:~$ dmesg | grep -e ndis -e wlan
[  184.668630] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[  184.976118] ndiswrapper: driver bcmwlhigh5 (Cisco Consumer Products LLC,03/28/2011, 5.100.68.46) loaded
[  185.293376] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011d6b000, 16000, 4
[  185.293390] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011d6ee80, 16000, 5
[  185.293397] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011d72d00, 16000, 5
[  185.293404] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011d76b80, 16000, 5
[  185.293409] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011d7aa00, 16000, 5
[  185.293415] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011d7e880, 16000, 5
[  185.293420] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011d82700, 16000, 5
[  185.293429] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011d86580, 16000, 5
[  185.293435] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011d8a400, 16000, 5
[  185.293440] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011d8e280, 16000, 5
[  185.293446] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011d92100, 16000, 4
[  185.293451] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011d95f80, 16000, 5
[  185.293457] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011d99e00, 16000, 5
[  185.293463] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011d9dc80, 16000, 5
[  185.293468] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011da1b00, 16000, 5
[  185.293474] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011da5980, 16000, 5
[  185.293479] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011da9800, 16000, 5
[  185.293487] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011dad680, 16000, 5
[  185.293493] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011db1500, 16000, 5
[  185.293498] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011db5380, 16000, 5
[  185.293504] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011db9200, 16000, 5
[  185.293509] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011dbd080, 16000, 4
[  185.293515] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011dc0f00, 16000, 5
[  185.293520] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011dc4d80, 16000, 5
[  185.293528] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011dc8c00, 16000, 5
[  185.293534] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011dcca80, 16000, 5
[  185.293539] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011dd0900, 16000, 5
[  185.293545] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011dd4780, 16000, 5
[  185.293550] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011dd8600, 16000, 5
[  185.293556] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011ddc480, 16000, 5
[  185.293561] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011de0300, 16000, 5
[  185.293567] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011de4180, 16000, 4
[  185.293573] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011de8000, 16000, 4
[  185.293580] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011debe80, 16000, 5
[  185.293586] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011defd00, 16000, 5
[  185.293592] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011df3b80, 16000, 5
[  185.293597] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011df7a00, 16000, 5
[  185.293602] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011dfb880, 16000, 5
[  185.293608] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011dff700, 16000, 5
[  185.293613] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011e03580, 16000, 5
[  185.293619] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011e07400, 16000, 5
[  185.293627] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011e0b280, 16000, 5
[  185.293633] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011e0f100, 16000, 4
[  185.293638] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011e12f80, 16000, 5
[  185.293644] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011e16e00, 16000, 5
[  185.293649] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011e1ac80, 16000, 5
[  185.293655] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011e1eb00, 16000, 5
[  185.293660] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011e22980, 16000, 5
[  185.293666] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011e26800, 16000, 5
[  185.293673] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011e2a680, 16000, 5
[  185.311169] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[  185.581883] wlan0: ethernet device c0:c1:c0:5e:57:95 using NDIS driver: bcmwlhigh5, version: 0x564442e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 13B1:003A.F.conf
[  185.588693] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  185.591026] usbcore: registered new interface driver ndiswrapper
[  185.667661] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  185.668179] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  210.401871] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
noblesse@PC:~$ rfkill list all

---

### Post by noblesse on 2013-04-28
Update i disabled the security on my router and it was able to connect. But i will like to have some security on my router.

---

### Post by noblesse on 2013-04-30
> **chili555 said:**
> Let's check a few more things:```
dmesg | grep -e ndis -e wlan
rfkill list all
```Always; and spelling and all that stuff our teachers whined about. Who knew my 5th grade teacher was a Linux nerd!?

I was wondering will setting up a static ip address clear this problem?

---

### Post by chili555 on 2013-04-30
> **noblesse said:**
> I was wondering will setting up a static ip address clear this problem?I doubt it. What security is set on your router? I suggest WPA2 and not the tricky mixed mode WPA/WPA2. Please see attached.

---

### Post by noblesse on 2013-04-30
> **chili555 said:**
> I doubt it. What security is set on your router? I suggest WPA2 and not the tricky mixed mode WPA/WPA2. Please see attached.

It has always be set to WPA2-PSK [AES]

---

