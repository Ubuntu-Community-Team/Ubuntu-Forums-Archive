---
title: "Wireless Not Working"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by kierpaul on 2009-11-11
Hello Ubuntu Community,

I have trouble with my Zydas USB wireless card. It is recognized but does not seem to load the driver or firmware in the kernel for some reason. I went through the directions for opening a wireless ticket have posted the outputs below. This happened after upgrading to Karmic, was ok in 9.04. Any help with this will be greatly appreciated. Do I need to use Ndiswrapper? I tried this but Ndiswrapper seems to completely malfunction in so much that it causes my wireless USB to not be recognized. It seems it was looking for a zd1211ub firmware and other places it is looking for zd1211rw. Confusion! Here is the info on my system:  

MSI 865PE ICH5 Chipset (2GB Mem PENT 4)

 lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0ace:1215 ZyDAS WLA-54L WiFi
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


lsusb -nn | grep  
*no information on this command*


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

lsmod
*gives this info about wireless driver*

zd1211rw               45216  0 
ip_tables              11692  3 iptable_nat,iptable_mangle,iptable_filter
mac80211              210408  1 zd1211rw
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
x_tables               16544  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
cfg80211              130440  2 zd1211rw,mac80211


lsmod | grep zd1211rw
zd1211rw               45216  0 
mac80211              210408  1 zd1211rw
cfg80211              130440  2 zd1211rw,mac80211


dmesg

345.317787] serial8250: too much work for irq16
[  345.331110] serial8250: too much work for irq16
[  345.344433] serial8250: too much work for irq16
[  345.357760] serial8250: too much work for irq16
[  345.371080] serial8250: too much work for irq16
[  345.384408] serial8250: too much work for irq16
[  345.397728] serial8250: too much work for irq16
[  345.411047] serial8250: too much work for irq16
[  345.424370] serial8250: too much work for irq16
[  345.437693] serial8250: too much work for irq16
[  345.446266] serial8250: too much work for irq16
[  345.451015] serial8250: too much work for irq16
[  345.464339] serial8250: too much work for irq16
[  345.477663] serial8250: too much work for irq16
[  345.490984] serial8250: too much work for irq16
[  345.504312] serial8250: too much work for irq16
[  345.517630] serial8250: too much work for irq16
[  345.530953] serial8250: too much work for irq16
[  345.544280] serial8250: too much work for irq16
[ 1139.752310] usb 1-3: firmware: requesting zd1211/zd1211b_ub
[ 1139.759455] usb 1-3: Could not load firmware file zd1211/zd1211b_ub. Error number -2
[ 1139.759466] zd1211rw 1-3:1.0: couldn't load firmware. Error number -2


lshw -C network

*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: eth0
       version: 10
       serial: 00:16:17:4a:91:20
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.103 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:23 ioport:c800(size=256) memory:feafef00-feafefff memory:80000000-8000ffff(prefetchable)
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:6b:3b:e7:ca
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

vboxnet0  Interface doesn't support scanning.

iwlist scan wlan0

*no information due to network being down* (My Emphasis)


lsb_release -d

Description:	Ubuntu 9.10

uname -mr
2.6.31-14-generic i686


sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                           * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
There is already a pid file /var/run/dhclient.eth0.pid with pid 3250
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:17:4a:91:20
Sending on   LPF/eth0/00:16:17:4a:91:20
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:17:4a:91:20
Sending on   LPF/eth0/00:16:17:4a:91:20
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.103 from 192.168.1.1
DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.103 from 192.168.1.1
bound to 192.168.1.103 -- renewal in 298235 seconds.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.

---

### Post by kierpaul on 2009-11-16
Solved.....Installed Linux Mint 7 and everything works nicely. There is little difference between the two operating systems with the exception that things tend to work better with Mint. Ubuntu is a nice operating system, but after Intrepid Ibex, the upgrades take out things that were working well (graphics, wireless, virtual boxes, etc)and seem to be getting progressively worse. I will stay a member of this forum in case I can help some people, but I am done with Ubuntu for now. There will be no way to win people over from Windows with these kinds of problems.

---

### Post by soupowl on 2009-12-05
I agree, I have the same problem, it seems to relate to my ZyDAS WLA-54L wireless adaptor.  Does anyone know of a USB type wireless adaptor that works well with 9.10?  I'm thinking i may have to go back to jaunty otherwise, i can't help thinking they should have delayed the release of 9.10

---

