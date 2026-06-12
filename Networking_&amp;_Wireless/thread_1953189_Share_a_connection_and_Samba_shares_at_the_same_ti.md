---
title: "Share a connection and Samba shares at the same time."
date: 2012-04-05
forum: Networking &amp; Wireless
---

### Post by t1m88 on 2012-04-05
I have a computer with a direct connection to the internet (eth0), which I want to connect to a media player (*eth1*).
The problem is that I can't share folders and share an internet connection, from my pc to my media player, at the same time.

On Ubuntu 11.10 these are my settings on NetworkManager (GUI):
*Eth0* is always on 'Automatic DHCP' and this setting works, because I have a working internet connection.

When I put *eth1* on 'shared to other computers' my internet connection is shared to the media player, but I can't connect to SMB shares on my pc.
When I put *eth1* on 'manual' and I setup a static ip-address, the internet connection of my pc stops working when I switch on the media player. The SMB shares are available though.

Editing */etc/network/interfaces *hasn't been working and this is the (standard) output:
auto lo
iface lo inet loopback



When I put *eth1* on 'Shared to other computers' this is the output of ```
ifconfig
```eth0      Link encap:Ethernet  HWaddr 00:0e:2e:36:89:67  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe36:8967/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15407 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13739972 (13.7 MB)  TX bytes:2111390 (2.1 MB)
          Interrupt:20 Base address:0x1100 

eth1      Link encap:Ethernet  HWaddr 00:0f:fe:80:f8:0a  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:feff:fe80:f80a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:986 errors:0 dropped:0 overruns:0 frame:0
          TX packets:948 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:130523 (130.5 KB)  TX bytes:366431 (366.4 KB)
          Interrupt:17 

eth2      Link encap:Ethernet  HWaddr 00:08:a1:80:bf:02  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x1200 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4047 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4047 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:605488 (605.4 KB)  TX bytes:605488 (605.4 KB)



When I have a static ip-address this is the output of ```
ifconfig
```eth0      Link encap:Ethernet  HWaddr 00:0e:2e:36:89:67  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe36:8967/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54719 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45763 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59123097 (59.1 MB)  TX bytes:7916236 (7.9 MB)
          Interrupt:20 Base address:0x1100 

eth1      Link encap:Ethernet  HWaddr 00:0f:fe:80:f8:0a  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:feff:fe80:f80a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:128 (128.0 B)  TX bytes:10483 (10.4 KB)
          Interrupt:17 

eth2      Link encap:Ethernet  HWaddr 00:08:a1:80:bf:02  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x1200 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10892 (10.8 KB)  TX bytes:10892 (10.8 KB)
 

 How do I need to set this up?

---

### Post by hughr2005 on 2012-04-05
Depends. What are your system specs? Are you running Ubuntu in a VM?

---

### Post by t1m88 on 2012-04-05
My PC is al dualboot with Windows XP and Ubuntu 11.10. When I boot in windows my internet connection gets shared and smb shares are available for my media player.

My media player is an old xbox with XBMC.

My pc has two network cards. *eth0* for internet and *eth1* for the connection with my media player.

I guess with VM you mean a virtual machine like VirtualBox. This is not the case.

---

### Post by t1m88 on 2012-04-11
My eth0 connection uses DHCP and this is the connection information:
- IP Address 192.168.1.65
- Broadcast Address 192.168.1.255
- Subnet Mask 255.255.255.0
- Default Route 192.168.1.1
- Primary DNS 192.168.1.1


I tried giving eth1:
- IP Adress 192.168.1.2
- Default Route 192.168.1.1

Settings on my Xbox were:
- IP Address 192.168.1.3
- Default Gateway 192.168.1.1
- For DNS I tried: 
     194.134.5.5 (Provider)
     192.168.1.1 (Router)
     empty

I also tried giving eth1 these settings:
- IP Address 192.168.0.2
- Default Route 192.168.0.1

Settings on my Xbox were:
- IP Address 192.168.0.3
- Default Gateway 192.168.0.1
- For DNS I tried: 
     194.134.5.5 (Provider)
     192.168.1.1 (Router)
     192.168.0.1
     empty

Every time eth1 connects the internet connections from eth0 doesn't work any more. When I disconnect eth1 the internet connection works immediately.

So when I configure eth1 manually in NetworkManager on Ubuntu 11.10 my static IP Address settings aren't correct, because they brake down the internet. It gives me access to my SMB shares however, but my purpose is to have a working internet connection on my PC and on my Xbox at the same time and be able to share media files.

How do I setup a correct static IP Address?

If things aren't clear please point them out and I will try to explain them.

---

### Post by t1m88 on 2012-04-18
Well the good thing is I got it working. Both my computer and my Xbox are heaving an internet connection and I can acces files via SMB. The bad thing is I don't know what I changed from last time I tried. My settings now are *eth1* 'shared to other computers' and on my Xbox 'automatic DHCP'.

Although I would rather have it working with static IP's, I'll mark this one as solved.

---

