---
title: "Asus wl-138g linux driver problem"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by FoxIII on 2009-02-12
Just bought an asus wl-138g wireless card, and as with other people's problems, I cannot connect using wireless. I have been to;

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

but, when I type lspci, it says this about my wireless card;

01:08.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)

which obviously does not show me anything to do with the bcm driver. I downloaded the linux driver from the asus site, but when trying to install, I type: make clean and everything goes fine, but when I type: make, the error is;

```
Linux Directory is /lib/modules/2.6.27-11-generic/build
Linux Kernel Versions is 2.6.27-11-generic
make -C /lib/modules/2.6.27-11-generic/build CROSS_COMPILE= M=/home/foxy/src/linuxsta/src/wl/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/foxy/src/linuxsta/src/wl/linux/wlc_led.o
In file included from /home/foxy/src/linuxsta/src/wl/linux/wlc_led.c:17:
/home/foxy/src/linuxsta/src/wl/linux/../../include/typedefs.h:166: error: conflicting types for ‘bool’
include/linux/types.h:33: error: previous declaration of ‘bool’ was here
In file included from /home/foxy/src/linuxsta/src/wl/linux/../../include/linux_osl.h:21,
                 from /home/foxy/src/linuxsta/src/wl/linux/../../include/osl.h:24,
                 from /home/foxy/src/linuxsta/src/wl/linux/wlc_led.c:19:
/home/foxy/src/linuxsta/src/wl/linux/../../include/linuxver.h:19:26: error: linux/config.h: No such file or directory
/home/foxy/src/linuxsta/src/wl/linux/../../include/linuxver.h:94:28: error: pcmcia/version.h: No such file or directory
make[2]: *** [/home/foxy/src/linuxsta/src/wl/linux/wlc_led.o] Error 1
make[1]: *** [_module_/home/foxy/src/linuxsta/src/wl/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [default] Error 2
```

I have also tried using the XP drivers from the disk using ndiswrapper, but this just freezes my computer and I cannot log in. I am currently working using eth0.

Any ideas?

TIA

---

### Post by jellyfisharepretty on 2009-06-13
I would also like to know if anyone has a solution.  I have the exact same problem.  Ndiswrapper simply will not work for me (says the hardware is not present) and the b43 driver is buggy, giving me a much lower speed than normal.

Same problem now using 2.6.28-11-generic, with build-essential installed.

---

### Post by toocer on 2009-07-14
I have the same problem..

lshw -C network gives me this

 [HTML]
  *-network:0             
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0e:a6:e0:b9:34
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=10.249.240.107 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 13
       bus info: pci@0000:00:13.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d2:b1:de:99:3f:99
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:18:f3:f8:47:42
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
[/HTML]

cat /etc/network/interfaces gives me

[HTML]auto lo
iface lo inet loopback[/HTML]

and iwconfig gives me

[HTML]wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/HTML]

i have tried the restricted driver.. the ndis driver and i cant get none to work.. i know i had it working under hardy .. but i don't want to install hardy ;)

I would be thankful for help with this.. iam lost..

---

