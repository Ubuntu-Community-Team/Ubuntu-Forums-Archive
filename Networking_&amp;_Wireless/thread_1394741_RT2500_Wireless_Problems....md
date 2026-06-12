---
title: "RT2500 Wireless Problems..."
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by jimisrvrox on 2010-01-31
ok guys...heres my issue. Im using 9.10 and dmesg shows:

[HTML][   47.113489] ADDRCONF(NETDEV_UP): wlan2: link is not ready[/HTML]

lspci

[HTML]01:08.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
[/HTML]

lshw -c network

[HTML]*-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth1
       version: a1
       serial: 00:e0:4c:b1:ec:16
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.103 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:22 memory:e7000000-e7000fff ioport:d400(size=8)
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: wmaster0
       version: 01
       serial: 00:0f:66:73:cb:b6
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:e6000000-e6001fff
[/HTML]

lsmod

[HTML]rt2500pci              15356  0 
rt2x00pci               7900  1 rt2500pci
rt2x00lib              29756  2 rt2500pci,rt2x00pci
[/HTML]

kernal

[HTML]2.6.31-17-generic i686
Ubuntu 9.10[/HTML]

iwconfig

[HTML]lo        no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan2     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/HTML]

ifconfig

[HTML]eth1      Link encap:Ethernet  HWaddr 00:e0:4c:b1:ec:16  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:feb1:ec16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:105140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55972 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:155829099 (155.8 MB)  TX bytes:4193101 (4.1 MB)
          Interrupt:22 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:340 (340.0 B)  TX bytes:340 (340.0 B)

wlan2     Link encap:Ethernet  HWaddr 00:0f:66:73:cb:b6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan2:avahi Link encap:Ethernet  HWaddr 00:0f:66:73:cb:b6  
          inet addr:169.254.8.239  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-0F-66-73-CB-B6-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/HTML]

iwlist scan 

[HTML]lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan2     No scan results
[/HTML]

ok so theres the info that I can think of. I forget what the command is to see what driver the wireless is using but the only thing I can think is that theres two modules for the rt loaded so it could be that. Anyways...nm says disconnected..any help would be surely appreciated as ive been hassling with this thing to get it working for a couple of days now. Thank you.

---

### Post by bkratz on 2010-01-31
Haven't had much experiece with the RT2500, but from your listing above this is your driver: driver=rt2500pci

Here is a similar thread where Chili555 (this output looks a lot like yours) said to try the following:

sudo modprobe rt2500pci
iwconfig

[http://ubuntuforums.org/showpost.php?p=8711658&postcount=2](http://ubuntuforums.org/showpost.php?p=8711658&postcount=2)

---

### Post by chili555 on 2010-01-31
Please see here:> eth1      Link encap:Ethernet  HWaddr 00:e0:4c:b1:ec:16  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
Also see here:  [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

Especially:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their *connection has has been **managed** for them*; they should simply see uninterrupted network connectivity.If you want the wireless to work, I'd suggest you disconnect the ethernet cable first. It may take a reboot.

You are being 'managed!'

---

