---
title: "Broadcom BCM4322 - network UNCLAIMED Lucid"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by jschille on 2010-05-11
I go to System-->Admin-->Hardware Drivers and it says my Braodcom STA driver is installed.  But when I run the command it says it's unclaimed..

```

*-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:22:19:f7:92:be
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=192.168.1.6 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:20 memory:f0888000-f0888fff ioport:30d0(size=8) memory:f0889c00-f0889cff memory:f0889800-f088980f
  *-network UNCLAIMED
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f0403fff

```

Also, when I click on my wireless options 
(top right hand corner) I can only see Wired connections.
Wireless Connections do not even come up.

---

### Post by jdquark on 2010-05-11
Hi,

I also have the same issue.  I just went through a new install of 10.04, and have the same wireless card.  It is registering under eth1 instead of wlan0.

I tried compiling wl.ko from the broadcom web page.  It did compile.  I then removed the unwanted items, b43 etc and installed, but to no avail.  

I removed everything and installed the Broadcom STA wireless driver; it says it is active and working, but the network does not see the wireless card.  

I tried adding eth1 to /etc/network/interfaces, did not work.

lspci | grep Network

0e:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

iwgetid 
eth1:avahi  ESSID:""

$iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:44 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:24:e8:c7:50:2e  
          inet addr:131.225.56.130  Bcast:131.225.56.255  Mask:255.255.255.0
          inet6 addr: fec0::a:224:e8ff:fec7:502e/64 Scope:Site
          inet6 addr: 2002:83e1:aa5b:a:224:e8ff:fec7:502e/64 Scope:Global
          inet6 addr: 2002:83e1:381e:a:224:e8ff:fec7:502e/64 Scope:Global
          inet6 addr: fe80::224:e8ff:fec7:502e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:209519 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25868098 (25.8 MB)  TX bytes:5302594 (5.3 MB)
          Interrupt:32 

eth1      Link encap:Ethernet  HWaddr 00:24:2c:88:a5:54  
          inet6 addr: fe80::224:2cff:fe88:a554/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1:avahi Link encap:Ethernet  HWaddr 00:24:2c:88:a5:54  
          inet addr:169.254.7.77  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2904 (2.9 KB)  TX bytes:2904 (2.9 KB)



Any ideas would be helpful.   I see it works for some people, would love to know the secret.

Cheers,
Jeff

---

### Post by Tsu Do Nym on 2010-05-11
See my post at [http://ubuntuforums.org/showthread.php?t=1479176](http://ubuntuforums.org/showthread.php?t=1479176).
Might be related.

---

### Post by jschille on 2010-05-11
> **Tsu Do Nym said:**
> See my post at [http://ubuntuforums.org/showthread.php?t=1479176](http://ubuntuforums.org/showthread.php?t=1479176).
Might be related.

nah, thank you for the reply though.
still unclaimed

---

### Post by jdquark on 2010-05-11
Thanks for the suggestion, but it did not work for me either.

Cheers,
Jeff

---

