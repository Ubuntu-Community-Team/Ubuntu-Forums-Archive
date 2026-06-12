---
title: "Wireless problem -- rfkill a '2' with switch 'on'"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by brettburtner on 2010-06-05
Hello.  Absolute newbie here having problems wiping my laptop completely of the dark side (Windows).

I need help getting my wireless working.  Any help would be greatly appreciated.  I really want to use this whole drive (all massively-huge 40GB worth) for Ubuntu, and be rid of Microsoft forever if possible.

My wireless works for awhile in Ubuntu, then, after a bit, it stops.  When it is working, my wireless light is on, and the value of 'rfkill' file is a zero (0).  After it stops working, the light is off, and the 'rfkill' file holds a two (2).

The only way I can get the wireless working again is to boot into Windows, at which time the wireless starts working again very quickly.  Once Windows turns on the wireless, I'm free to restart into Ubuntu and -- once again -- wireless is working and rfkill=0.

There doesn't seem to be any pattern as to why/when the wireless light goes off.  And, using Windows to turn it on always works.

Any ideas?

Here is what I've got as a result of lshw -C network:

  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:08:91:d8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:10 ioport:a000(size=256) memory:d0001000-d00010ff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:63:e3:16
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=128 maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
       resources: irq:10 memory:d0000000-d0000fff

And here is the output of iwconfig when wireless is working:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:4A:F1:FF   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/100  Signal level=-71 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:0   Missed beacon:6

Thanks in advance for any help.

---

