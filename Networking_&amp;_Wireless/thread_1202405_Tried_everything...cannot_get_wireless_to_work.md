---
title: "Tried everything...cannot get wireless to work"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by stanggt3 on 2009-07-02
On my gateway mx7515 laptop I cant get the wireless working.

I cant get the blue wireless light on at all, but Ive read that it doesnt matter, it will work without that light.

I have the newest Ubuntu, I just installed it to give it a shot (im a first time user...the easier the directions the better!)

Ive tried these...maybe im doing something wrong.  I have the 4318 card.

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by superprash2003 on 2009-07-02
post output of
1)lshw -C network
2)iwconfig

---

### Post by The Toxic Mite on 2009-07-02
> **superprash2003 said:**
> post output of
1)lshw -C network
2)iwconfig

Let me make this clearer:

Go to Applications > Accessories > Terminal, and enter the following commands:

```

lshw -c network
iwconfig

```

Post the outputs of these when you are done :D

---

### Post by stanggt3 on 2009-07-02
First one....

randy@randy-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:03:25:28:67:8c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:03:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:45:8c:cd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 12:ef:12:b2:b0:eb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


2nd one....

randy@randy-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by The Toxic Mite on 2009-07-02
Right, I can't go any further (I have more experience dealing with Atheros cards - my laptop has one :P)

Good luck in finding a solution. :)

---

### Post by stanggt3 on 2009-07-03
Anyone....I really wanna work on this before switching back

---

### Post by superprash2003 on 2009-07-03
check this out [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

