---
title: "Dell C600 and Linksys wpc11 ver 3"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by jtraceypgh on 2011-02-15
I'm brand new to Ubuntu and wasn't sure where to post this as it applies to a couple categories.  Since it involves a Dell machine, I thought this was probably the best place to start...

I installed Ubuntu 10.10 on this machine yesterday.  Have found help correcting the video to 1024x768 through the forum, but have not found an answer to the wireless card.  It sees the network router but will not connect, regardless of router security settings (WEP or none).  With WEP active, it asks for the key, but after it's entered it seems to be trying to connect but eventually returns the dialog box asking for the key.  To correct the video a post provided a revised configuration file to be inserted into the system (I have EXTREMELY limited understanding of programing).  Is any such option available to correct the wireless card issue?  Any suggestions would be appreciated!

FYI after posting I found the card doesn't work on my IBM where I started testing UBUNTU by running it inside Windows.  Must not be strictly a Dell issue.

Thanks in advance!

---

### Post by jtraceypgh on 2011-02-17
After looking at the HOWTO post a Wireless issue Sticky, I retrieved the following.  It appears to me (just guessing!) that there are two different wireless devices (wlan0 and wifi0)created in Ubuntu for a single PCMCIA card.  Are these in conflict, thus the problem?  If so, can one be deleted somehow??

Thanks again, and here's the "stuff"...


New Note 4

Wireless issue details for posting

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:76:49:9e:c8  
          inet addr:192.168.10.164  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::204:76ff:fe49:9ec8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1716 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2368596 (2.3 MB)  TX bytes:238932 (238.9 KB)
          Interrupt:11 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:808 errors:0 dropped:0 overruns:0 frame:0
          TX packets:808 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63672 (63.6 KB)  TX bytes:63672 (63.6 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-06-25-11-4D-E2-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:3 Base address:0x100 

wlan0     Link encap:Ethernet  HWaddr 00:06:25:11:4d:e2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:3 Base address:0x100 

iwconfig wlan0
wlan0     IEEE 802.11b  ESSID:"\x05\xEF\xF7"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-73 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:15  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:48   Missed beacon:0

iwconfig wifi0
wifi0     IEEE 802.11b  ESSID:"\x05\xEF\xF7"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off

The below was reported at the end of a lengthy list that resulted from running the dmesg command.  It seemed significant...

[ 6315.364076] pcmcia_socket pcmcia_socket1: pccard: PCMCIA card inserted into slot 1
[ 6315.364378] pcmcia 1.0: pcmcia: registering new device pcmcia1.0 (IRQ: 3)
[ 6315.366274] hostap_cs: setting Vcc=33 (constant)
[ 6315.366334] Checking CFTABLE_ENTRY 0x01 (default 0x01)
[ 6315.366342] IO window settings: cfg->io.nwin=1 dflt->io.nwin=1
[ 6315.366350] io->flags = 0x0046, io.base=0x0000, len=64
[ 6315.370781] hostap_cs: Registered netdevice wifi0
[ 6315.410886] hostap_cs: index 0x01: , irq 3, io 0x0100-0x013f
[ 6315.610447] prism2_hw_init: initialized in 200 ms
[ 6315.611392] wifi0: NIC: id=0x801b v1.0.0
[ 6315.611557] wifi0: PRI: id=0x15 v1.1.0
[ 6315.611708] wifi0: STA: id=0x1f v1.4.2
[ 6315.614230] wifi0: defaulting to bogus WDS frame as a workaround for firmware bug in Host AP mode WDS
[ 6315.614245] wifi0: Warning: secondary station firmware version 1.4.2 does not seem to work in Host AP mode
[ 6315.621665] wifi0: registered netdevice wlan0
[ 6315.657803] ADDRCONF(NETDEV_UP): wifi0: link is not ready
[ 6315.657922] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6315.673774] wlan0: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
[ 6315.685179] wifi0: LinkStatus=2 (Disconnected)
[ 6315.709220] wifi0: LinkStatus: BSSID=44:44:44:44:44:44

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 3c556 Hurricane CardBus [Cyclone]
       vendor: 3Com Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 10
       serial: 00:04:76:49:9e:c8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.10.164 latency=32 link=yes maxlatency=5 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:d400(size=256) memory:f3ffdc00-f3ffdc7f memory:f3ffd800-f3ffd87f memory:fc000000-fc01ffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:06:25:11:4d:e2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=hostap firmware=1.4.2 multicast=yes wireless=IEEE 802.11b

---

### Post by jtraceypgh on 2011-02-21
It occurred to me to try this on a different router.  Lo and behold it worked fine in both the Dell and my IBM.  Must be my home router...

---

