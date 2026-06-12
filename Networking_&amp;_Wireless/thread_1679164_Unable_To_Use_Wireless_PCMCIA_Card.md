---
title: "Unable To Use Wireless PCMCIA Card"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by Meaple on 2011-01-31
I have tried to find a solution myself and I can't. I have looked all over the place and found nothing that resembles a solution. The problem is I can't install the driver for my wireless card since I get these errors:
```
make -C tools
make[1]: Entering directory `/home/froogle/Downloads/driver/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/froogle/Downloads/driver/tools'
/home/froogle/Downloads/driver/tools/bin2h
cp -f os/linux/Makefile.6 /home/froogle/Downloads/driver/os/linux/Makefile
make  -C  /lib/modules/2.6.32-28-generic/build SUBDIRS=/home/froogle/Downloads/driver/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-28-generic'
  CC [M]  /home/froogle/Downloads/driver/os/linux/../../common/rtmp_init.o
  CC [M]  /home/froogle/Downloads/driver/os/linux/../../common/cmm_info.o
/home/froogle/Downloads/driver/os/linux/../../common/cmm_info.c: In function ‘RTMPIoctlGetSiteSurvey’:
/home/froogle/Downloads/driver/os/linux/../../common/cmm_info.c:1922: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/home/froogle/Downloads/driver/os/linux/../../common/cmm_info.c:1922: error: (Each undeclared identifier is reported only once
/home/froogle/Downloads/driver/os/linux/../../common/cmm_info.c:1922: error: for each function it appears in.)
/home/froogle/Downloads/driver/os/linux/../../common/cmm_info.c:1922: error: implicit declaration of function ‘signal_pending’
/home/froogle/Downloads/driver/os/linux/../../common/cmm_info.c:1922: error: implicit declaration of function ‘schedule_timeout’
make[2]: *** [/home/froogle/Downloads/driver/os/linux/../../common/cmm_info.o] Error 1
make[1]: *** [_module_/home/froogle/Downloads/driver/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-28-generic'
make: *** [LINUX] Error 2

```I have no idea what this means at all and would be a great help as well. Here is a bit of info about the card and other things to help diagnose the issue. If you need anything else just ask and thanks in advance.

[U][B]Edimax EW-7708Pn
[/B][/U]
        Network controller: RaLink RT2800 802.11n PCI
        Subsystem: RaLink Device 2860
        Flags: bus master, slow devsel, latency 64, IRQ 21
        Memory at 4c000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: rt2860
        Kernel modules: rt2860sta[U][B]

$ ifconfig wlan0

[/B][/U]wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 
[U][B]
$ lsmod | grep rt28[/B][/U]

rt2860sta             481561  0 

_**$ sudo lshw -C network**_

*-network DISABLED
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=RT2860 Wireless
       resources: irq:21 memory:4c000000-4c00ffff

---

