---
title: "No Wlan0 present?"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by Mastermind1980 on 2009-11-05
Ok, here is what I did:

1. I downloaded and installed ndisgtk.
2. I got the WPN111 v2.0 Netgear drivers like they told me to in the Ndiswrapper Wiki.
3. I started Windows Wireless Drivers (ndisgtk) I added the file WPN111vx.inf. It said that its unable to see if the hardware is present. I rebooted and started the program again, same story.
4. The strange thing is that when I click away the Error with 'Ok' it sais: Hardware Present?: Yes.
5. Now I did the following commands:

```
mastermind@mastermind-Linux:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 07b8:e004 D-Link Corp. Mass Storage Device
**Bus 001 Device 004: ID 1385:5f01 Netgear, Inc WPN111 (no firmware)**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 04d9:1133 Holtek Semiconductor, Inc. 
Bus 002 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```And:

```
mastermind@mastermind-Linux:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:92:83:c7:6b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.4 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 ioport:e800(size=256) memory:febff000-febfffff memory:febc0000-febdffff(prefetchable)

```And also:

```
mastermind@mastermind-Linux:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wpn111vx : driver installed
    device (1385:5F01) present

```Another one:

```
mastermind@mastermind-Linux:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

```And least but not last:

```
mastermind@mastermind-Linux:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```As I see here there is no Wlan0.... Also the flash on my WPN111 isnt flashing, it also keeps cold, normally it becomes warm if active.

I installed it trough the Console too, it got wrong on -m and setting it up:
 
 ```
mastermind@mastermind-Linux:/etc/modprobe.d$ sudo ndiswrapper -m
 [sudo] password for mastermind: 
 WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
 adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
 
 mastermind@mastermind-Linux:/etc/modprobe.d$ ifconfig wlan0 up
 wlan0: ERROR while getting interface flags: No such device
```

I have no problem with LAN and Im just a few meters away from the router, also I have perfect internet on Windows XP, Vista and 7.

Anybody a clue?

---

### Post by Tom Handsy on 2009-11-06
hmm, you can try using VMware, then all drivers and **** will be installed correctly and you will get internet just as fast as host system

---

### Post by Mastermind1980 on 2009-11-06
I dont have any usage on that, that means still running windows but then sharing my specs with ubuntu, I dont think thats the exact thing Im looking for.

Thanks for the reply anyways!

---

### Post by Mastermind1980 on 2009-11-08
Bumperdebumpbumpbump

---

### Post by pastalavista on 2009-11-08
You might check in /etc/modprobe.d and look at the blacklist.conf and other blacklist files to make sure your device or driver hasn't been blacklisted. If it has, just comment it out (#).

---

### Post by Mastermind1980 on 2009-11-09
will do/try, thanks for your response

---

### Post by Mastermind1980 on 2009-11-13
Bump

---

