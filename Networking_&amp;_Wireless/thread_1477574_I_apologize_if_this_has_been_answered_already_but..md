---
title: "I apologize if this has been answered already but....."
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by ooelectronoo on 2010-05-08
My lan connection to my router isn't working i have it plugged in the cable is good ( fyi i do have some computer knowledge) 
So my wireless is working right when i booted up but my lan is not. i have a @#$^ i am afraid to say what it is lol dell    with their integrated ethernet card. OS: ubuntu 10.04    everything works fine but the wired connection. 
Dlink router with all of the settings made properly. i read somewhere about doing a whole bunch of stuff but i thought that since this was a higher version they would have that problem fixed............................Boy Was I Wrongggg! lol any help would be loverly. i also have aim or msn whichever is more preferred. i hopefully will be notified that someone has responded to this thread.



Thank you in advance for helping/trying to resolve my issues.

---

### Post by steveneddy on 2010-05-08
model number of PC

is this a Dell server or a desktop version?

---

### Post by Iowan on 2010-05-09
Wireless => laptop?
From a terminal (Applications>Accessories>Terminal) check: ```
sudo lshw -C network
```Post results. :)

---

### Post by ooelectronoo on 2010-05-09
dell dimension  9100 desktop 


results of command:

 *-network:0             
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wlan0
       version: 01
       serial: 00:0f:3d:a8:bf:a3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.0.166 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:efbf0000-efbfffff
  *-network:1
       description: Ethernet interface
       product: N10/ICH 7 Family LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:70:67:7e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:efbef000-efbeffff ioport:ccc0(size=64)

---

### Post by Iowan on 2010-05-09
Drivers are still not my forte, but I found [this]("http://www.linuxquestions.org/questions/linux-hardware-18/dell-dimension-9100-ethernet-problem-348164/") link about the Dimension 9100 ethernet.

---

### Post by ooelectronoo on 2010-05-09
> **Iowan said:**
> Drivers are still not my forte, but I found [this]("http://www.linuxquestions.org/questions/linux-hardware-18/dell-dimension-9100-ethernet-problem-348164/") link about the Dimension 9100 ethernet.


I have followed the instrucions from what that thread said and i got all the way to the make install and this is what i got

make -C /lib/modules/2.6.32-22-generic/build SUBDIRS=/usr/local/src/e100-3.5.17/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in "/usr/local/src/e100-3.5.17/src/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/usr/local/src/e100-3.5.17/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [default] Error 2


p.s. i had to sudo make install it due to its in the usr/local/src folder lol

---

