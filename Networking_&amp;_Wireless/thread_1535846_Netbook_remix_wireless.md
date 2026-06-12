---
title: "Netbook remix wireless"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by rhyz on 2010-07-21
I have a WLI-PCM-L11G wireless card that has worked in previous editions of ubuntu example of 8.10 9.04

But in 10.04 i cant seem to connect to a wireless network i can see a list of available networks i click on BTFON which is a hotspot no password needed i wait a little bit and it says im not connected!

I have also tried another network i know the password to but after a min it asks for the password again ?!?

Any ideas on how to fix ??? (i am fully updated as of yesterday! via cable!)

Thanks

---

### Post by rhyz on 2010-07-22
So i havent heard anything :/ but i have some more info if it helps!!!

Output of iwconfig:
```

rhys@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"BTFON"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:1
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Output of lshw -C network:
```

rhys@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:b6:df:72
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:10 ioport:8c00(size=256) memory:ec002800-ec0028ff
  *-network
       description: WLI-PCM-L11
       product: Version 01.01
       vendor: MELCO
       physical id: 0
       slot: Socket 0
       resources: irq:3
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:4f:ae:b6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b

```

I would really use ubuntu if i could just get on the internet with it!!!

Thanks :D

---

### Post by rhyz on 2010-07-24
Bump!!!!

---

### Post by rhyz on 2010-07-25
Sorry BUMP!!!!! :(

---

### Post by rhyz on 2010-07-27
Bump bump buuuuuuuuuummmmpp !!!!!!!!!!!!!!!!!!!!!

---

### Post by rhyz on 2010-07-28
B
u
m
p
!
!
!

---

### Post by rhyz on 2010-07-29
Hello

As i have had absolutley no responce i tried wicd

i have removed network-manager and installed wicd instead

with wicd i can see all wireless conections and i know i can connect to btfon hotspot unsecure! but i am still having trouble connecting to the houses wifi and says i have a bad password!?

So with wicd i am one step further being able to connect to the hotspots! but still cant connect to own wifi

Please help THanks

---

