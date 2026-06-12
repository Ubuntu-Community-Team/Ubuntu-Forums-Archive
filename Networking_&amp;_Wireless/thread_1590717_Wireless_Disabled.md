---
title: "Wireless Disabled"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by theleica on 2010-10-08
Heya,

I've just managed to get hold of a friend's old laptop and I thought this'd be a great way to try out Ubuntu.

I've installed 10.04 on a HP 510 laptop with an Intel 2200BG [Calexico2] Wireless card installed. Unfortunately HP did something rather silly on this laptop and put a lovely little wireless button on it, which (since installing Ubuntu) seems to be causing problems.

So in the menubar 'Enable Wireless' is greyed out and pressing the button doesn't seem to change anything. I've booted up the BIOS and tried to see if there's a way to enable the wireless from there, but there doesn't seem to be a way. 

I've installed all the updates by using a wired connection, but a wired connection really is a pain as it's nowhere near my desk.

I'm not that versed in using command line to modify anything, so I'm afraid any instructions would have to be rather explicit.

If anyone could help me get a wireless connection up and running, that'd be amazing.

Much thanks!

---

### Post by dineshs on 2010-10-08
Please post the results of(applications-accessories-terminal)
```
sudo lshw -C network
```
```
iwconfig
```
and have a look [here]("http://fostergrant.ubuntuforums.org/showthread.php?p=9288622")

---

### Post by theleica on 2010-10-08
```
 *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:c7:79:09
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.109 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
       resources: irq:21 memory:d0000000-d0000fff
  *-network:1
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:16:d4:be:a7:59
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.2.3 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:d0002000-d0002fff ioport:2000(size=64)

```

And

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Caer Sidhe"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: D8:30:62:34:BA:FF   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=84/100  Signal level=-30 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:15

```

I think I tried a lot in that thread already, I'll go through it again and try it again though - thanks.

---

### Post by theleica on 2010-10-08
I take it back, i installed the Ndiswrapper and it's gotten my wifi working. Perfect!

Thank you for that link, must be just about the only wifi related Ubuntu post I hadn't looked through yet!

---

### Post by dineshs on 2010-10-08
Thanks to chili555
please mark the thread as solved via thread tools

---

