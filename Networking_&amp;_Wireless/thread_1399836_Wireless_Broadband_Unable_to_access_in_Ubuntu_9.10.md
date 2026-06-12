---
title: "Wireless Broadband Unable to access in Ubuntu 9.10"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by Jinu Thomas on 2010-02-06
Hi All,
 
I am another newbie to Linux Ubuntu. **I've installed Ubuntu 9.10** along with Windows 7. I have a wireless broadband connection which works with Windows very well. But, when I am trying to access internet through my wireless broadband in Ubuntu, I don't see any wireless network on the top right hand corner. It has a network icon but, doesn't show wireless network under it.
 
I checked uner Hardware drivers that there are no drivers it displays. It is blank.
 
I've run some of the command to give you all the idea about my network card.
 

**$ lspci**
Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 
VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 
Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 
USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 
USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 
USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 
USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 
Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 
PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 
PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 
PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 
PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 
USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 
USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 
USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 
USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 
PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 
ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 
SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 
SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
04:00.0 
Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
08:00.0 
Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 
FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 
SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 
System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 
System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
 
[B]$ sudo apt-get install b43-fwcutter
[/B]Reading 
package lists... 
Done
Building dependency tree       
Reading state information... 
Done
E: Couldn't find package b43-fwcutter
 
**Please let me know what to be done to configure my wireless broadband in Ubuntu to access internet.**
 
Thanks in advance
 
Regards
Jinu

---

### Post by northd_tech on 2010-02-06
> **Jinu Thomas said:**
> Hi All,
 
I am another newbie to Linux Ubuntu. I've installed Ubuntu 9.10 along with Windows 7. 
...
**$ lspci**
...
Network controller: **Broadcom Corporation BCM4312** 802.11b/g (rev 01)
08:00.0 
Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 


That's a Broadcom 4312 (which should be very easy to install using the Broadcom STA driver).

I'm not sure if the b43-fwcutter that you tried to install will cause any problems, but I would start at this thread first:

The Definitive 9.10 Broadcom Solution Guide
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

Also, you could download the STA driver (that should work very well for the Broadcom 4311, **4312**, 4321, & 4322 WiFi) directly from Broadcom at:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

It might also help if you post the output of the following commands:

```
lsmod

uname -a

sudo lshw -C network

ifconfig

iwconfig

```

Edit:  Also see this long thread:

[B]How to install native broadcom drivers for  BCM4311, BCM4312, BCM4321, and BCM4322
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)
[/B]

---

### Post by Jinu Thomas on 2010-02-06
> **northd_tech said:**
>  
Edit: Also see this long thread:
 
**How to install native broadcom drivers for BCM4311, BCM4312, BCM4321, and BCM4322**
**[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)**

 
I tried the above URL to setup broadcom drivers for BCM4312 but, it resulted in the following error while creating kl.o file.
 
 
Error:::::::
------------
 
/usr/jinu/wdriver# make -C /lib/modules/2.6.31-14-generic/build M=`pwd`
make: 
Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
 
LD /usr/jinu/wdriver/built-in.o
 
CC [M] /usr/jinu/wdriver/src/wl/sys/wl_linux.o
 
CC [M] /usr/jinu/wdriver/src/wl/sys/wl_iw.o
 
CC [M] /usr/jinu/wdriver/src/shared/linux_osl.o
 
LD [M] /usr/jinu/wdriver/wl.o
ld: Relocatable linking with relocations from format elf64-x86-64 (/usr/jinu/wdriver/lib/wlc_hybrid.o_shipped) to format elf32-i386 (/usr/jinu/wdriver/wl.o) is not supported
make[1]: *** [/usr/jinu/wdriver/wl.o] 
Error 1
make: *** [_module_/usr/jinu/wdriver] 
Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'

---

### Post by Jinu Thomas on 2010-02-06
Following are the details asked:
 
# lsmod
Module                  Size  Used by
ieee80211_crypt_tkip     9276  0 
ieee80211_crypt         5024  1 
ieee80211_crypt_tkip
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_intelhdmi    12860  1 
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 
snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 
snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 
snd_pcm_oss
snd_pcm                75296  3 
snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
joydev                 10272  0 
sdhci_pci               7100  0 
snd_seq_oss            28576  0 
dell_wmi                2564  0 
snd_seq_midi            6432  0 
uvcvideo               59080  0 
mac80211              181236  0 
snd_rawmidi            22208  1 
snd_seq_midi
videodev               36736  1 
uvcvideo
snd_seq_midi_event      6940  2 
snd_seq_oss,snd_seq_midi
lp                      8964  0 
dell_laptop             8128  0 
sdhci                  17472  1 
sdhci_pci
ricoh_mmc               3676  0 
cfg80211               93052  1 
mac80211
iptable_filter          3100  0 
v4l1_compat            14496  2 
uvcvideo,videodev
psmouse                56180  0 
snd_seq                50224  6 
snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ip_tables              11692  1 
iptable_filter
dcdbas                  7292  1 
dell_laptop
serio_raw               5280  0 
snd_timer              22276  2 
snd_pcm,snd_seq
led_class               4096  1 
sdhci
snd_seq_device          6920  5 
snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport                35340  2 
ppdev,lp
x_tables               16544  1 
ip_tables
snd                    59204  17 
snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_dev
ice
soundcore               7264  1 
snd
snd_page_alloc          9156  2 
snd_hda_intel,snd_pcm
fbcon                  36640  72 
tileblit                2460  1
fbcon
font                    8124  1 
fbcon
bitblit                 5372  1 
fbcon
softcursor              1756  1 
bitblit
usbhid                 38208  0 
ohci1394               29900  0 
ieee1394               86596  1 
ohci1394
ssb                    35300  0 
tg3                   109600  0 
i915                  221064  3 
drm                   159584  3 
i915
i2c_algo_bit            5760  1 
i915
video                  19380  1 
i915
output                  2780  1 
video
intel_agp              27484  2 
i915
agpgart                34988  2 
drm,intel_agp
 

# uname -a
Linux jinu-jisha 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
 
# sudo lshw -C network
  
*-network               
       
description: Network controller
       
product: BCM4312 802.11b/g
   vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:04:00.0"]pci@0000:04:00.0[/EMAIL]
       version: 01
       width: 64 bits
       clock: 
33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f8000000-f8003fff
  
*-network
       
description: Ethernet interface
       
product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:08:00.0"]pci@0000:08:00.0[/EMAIL]
       logical name: eth0
       
version: 10
       serial: 00:26:b9:17:b2:7c
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list 
ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 
firmware=sb v2.17 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:30 memory:fc500000-fc50ffff
 
 
# ifconfig
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:b9:17:b2:7c  
          
UP BROADCAST MULTICAST  MTU:1500  Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000 
          
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          
Interrupt:17 
 
lo        Link encap:Local Loopback  
          
inet addr:127.0.0.1  Mask:255.0.0.0
          
inet6 addr: ::1/128 Scope:Host
          
UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:0 
          
RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by Jinu Thomas on 2010-02-07
Please help...... Ubuntu Masters................

---

### Post by PetoB on 2010-02-07
Hi all,

I will not make new thread, I will add my problem here...

1.) I was download Ubuntu Karmic Koala, install on Flash drive and install in my laptop Dell studio 1555, I was not able up and run my broadband wireless, I read tons of help here and everywhere but after million of re-installation and downloading and doing not understandable steps for me (I am simply lama or new-by like I read here) I am sick and tired... I try to run Ubuntu directly from my flash drive and there I found in Hardware drivers driver, I was activate him and all is work, but on installed linux I am not able to do it, I try to install manually but ask me for dkms package, I install it and after this I was able to install driver for wireless card, than I find driver not-activated in Hardware drivers and is not possible to activate... just ask me for password and then nothing...

...can somebody help me? ...if I will not fix this I will never learn linux, without wifi I will have no net and without net for me is only unusable space on my hard drive ;)

---

### Post by Beemo on 2010-02-07
You need the wl driver.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

the directions are in the README part. good luck.

-Beemo

---

### Post by PetoB on 2010-02-09
that I have downloaded, but totaly do not understand what to do... I have no experience with linux

I can install debian package :) but this is over my experience with linux a boot and reboot to and from win to find some help on internet is unusable

---

### Post by PetoB on 2010-02-10
So I manage to install this package from, but does not work, final decision, Linux is not for me. ...sad but true!

---

### Post by PetoB on 2010-02-11
:) so it is me again....

Just to clear, I deleted everything, I fomrated partition and I feel free... but I can  not sleep, because I was not manage install Ubuntu ...I was wake up at 3:00 and finally I have Win7 and Ubuntu up and run side by side with wifi, grafick card, compiz and so and so...

...whole time was problem, that Ubuntu start driver b43 and even when I did installation of driver from broadcom, it was not able to use wifi after reboot. need to be b43 added to blacklist and for the moment, everything looks OK - I hope this is my begining of friendship with Ubuntu - thanks to all which share experiences and to my friend sifu

---

