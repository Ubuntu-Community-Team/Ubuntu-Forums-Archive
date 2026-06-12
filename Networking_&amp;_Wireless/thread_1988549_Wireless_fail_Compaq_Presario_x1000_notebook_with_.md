---
title: "Wireless fail: Compaq Presario x1000 notebook with Intel WLAN WM382100 Card"
date: 2012-05-27
forum: Networking &amp; Wireless
---

### Post by keithwins on 2012-05-27
[My third post, below, notes that I've solved/worked around this. I might still be able to use some wisdom...]


I just switched from Ubuntu 9.03, I think (hadn't used this old notebook for years) that had a working wireless connection to lubuntu 12.04 (new ubuntu doesn't support non-PAE CPUs). Can't get the wireless working.

I installed b43 before I realized it's not a Broadcom chip (I don't think anyway) so that wasn't the right driver. I then removed B43 with Synaptic Package Manager. I read somewhere that the right driver is already installed with the kernel, I believe. I played the with Preferences/Network Connections and couldn't get anything to happen: seemed like it didn't see any wireless networks.

I downloaded Wicd, and it sees my wireless network (and several other nearby ones), but I can't get it to log on. The wireless security is just WEP (Verizon default... yes, I know), and lots of other things log into it just fine, but this notebook doesn't. When I set up Wicd with the passphrase, it gets all the way to "validating authentication" and then "failed: bad password". I've tried all the WEP options in Wicd. I've triple-checked (at least) my password.

I'm not very experienced at ubuntu/lubuntu, so I might be making a very basic mistake. My understanding is very partial, so if you have any ideas please spell them out as simply as you can. Thanks for any help.

---

### Post by keithwins on 2012-05-27
Here are the results asked for in the HOWTO post:

lspci: 02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

ifconfig:


eth0      Link encap:Ethernet  HWaddr 00:02:3f:64:1b:d1  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:3fff:fe64:1bd1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4110136 (4.1 MB)  TX bytes:235505 (235.5 KB)
          Interrupt:10 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:04:23:62:4a:ae  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Memory:90000000-90000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26682 (26.6 KB)  TX bytes:26682 (26.6 KB)


kw@kw-Compaq-Presario-X1000-DN585A-ABA:~$ iwconfig eth1
eth1      unassociated  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kw@kw-Compaq-Presario-X1000-DN585A-ABA:~$ iwconfig eth0
eth0      no wireless extensions.


lsmod doesn't return anything including the string wlan


dmesg returns a long list of these:

[21951.670645] ADDRCONF(NETDEV_UP): eth1: link is not ready
[21951.823133] ADDRCONF(NETDEV_UP): eth1: link is not ready
[21952.210607] 8139cp 0000:02:01.0: eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[21952.486912] 8139cp 0000:02:01.0: eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[21963.120043] eth0: no IPv6 routers present


sudo lshw -C network
[sudo] password for kw: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 20
       serial: 00:02:3f:64:1b:d1
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139cp driverversion=1.3 duplex=full ip=192.168.1.12 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:10 ioport:2000(size=256) memory:90300000-903000ff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 04
       serial: 00:04:23:62:4a:ae
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=128 link=no maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
       resources: irq:5 memory:90000000-90000fff



iwlist: cell01 is my wireless network:

          Cell 01 - Address: 00:26:B8:45:4D:00
                    ESSID:"3ECP2"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:67  Signal level:0  Noise level:0
                    Extra: Last beacon: 868ms ago


lsb_release -d
Description:	Ubuntu 12.04 LTS


sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...      


Well, there's everything that's suggested, sorry I didn't try to digest it much but I was afraid I'd edit out something important. Thanks for trying to help!

Keith

---

### Post by keithwins on 2012-05-27
I just went down to the wireless icon on the lower right of my screen, tried to connect from there, and it worked.

Any idea of why Wicd didn't work about 50 times in a row, or why preferences/Network Connections doesn't even show wireless networks? There might still be something important to fix. But I'm connected wirelessly writing this!

---

