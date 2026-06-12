---
title: "Wireless network is not visible"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by lukep1984 on 2011-01-14
Hello!

I'm using Ubuntu 9.10 and I've recently bought linksys wusb100v2 adapter to my desktop pc in order to connect to wireless network (linksys wag120n).
So far I have installed driver RT2870_STA following this instruction: [http://ubuntuforums.org/showthread.php?t=1342593&highlight=rt2870](http://ubuntuforums.org/showthread.php?t=1342593&highlight=rt2870).
The problem is that in wicd I can't see my wireless network and I could't also connect to my wireless network using network manager.
But I can connect to this network from other computer.

Below are some results from my console:
lsusb
Bus 001 Device 002: ID 1737:0078 Linksys 

lsmod | grep rt28
rt2870sta             554992  1 

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

ra0     Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist ra0 scan
ra0       No scan results

/etc/network/interfaces
auto lo
iface lo inet loopback

ifup ra0
Ignoring unknown interface ra0=ra0.

When I go to: System>Administration>Network Tools I can choose: Unknown Interface(ra0)

Now I changed /etc/network/interfaces to:
auto ra0
iface ra0 inet dhcp

and after executing:
ifup ra0
ifup: interface ra0 already configured

lsh -C network

  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: eth0
       version: 10
       serial: some MAC address
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.4 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:16 ioport:9000(size=256) memory:e7000000-e70000ff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: some MAC address
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.0.0 multicast=yes wireless=Ralink STA

The WPA Supplicant driver chosen in wicd advandced settings is wext. I can't see there installed RT2870STA, only ralink legacy. 
So maybe this is problem of this situation. But how change it eventually?

I don't have any clue what I can do more.
Please, help:-) Thanks for any tips.

Best Regards,
Luke

---

### Post by lukep1984 on 2011-01-15
So I upgraded Ubuntu to 10.04 and followed this instruction: 
[http://ubuntuforums.org/showthread.php?t=1434301](http://ubuntuforums.org/showthread.php?t=1434301)

And It works now:-)

Best regards,
Luke

---

