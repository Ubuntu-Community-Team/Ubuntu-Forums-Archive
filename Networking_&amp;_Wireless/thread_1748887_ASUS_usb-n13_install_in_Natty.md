---
title: "ASUS usb-n13 install in Natty"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by rhondabruce on 2011-05-04
I'll start by letting you know I'm definately a novice Ubuntu user but figured this would be the best place for this post. It took me a while to get wireless to work on my notebook through Karmic over a year ago but it was figured out. This USB device using Natty seems like a different animal. 

I read countless pages pertaining to this device on older Ubuntu versions and I'm kind of looking for a refreshment course with updated info using Natty. I believe I have the updated drivers but don't really know how to install them. FYI, I have no way to get an internet connection on this newly aquired desktop so I am using this notebook for reference info. Hopefully I haven't screwed anything up yet with my new 11.04 by using info in other posts. 

Anyway, so I purchased this Asus USB-n13 adapter and the computer does recognize it. However, I can't get it to work. A fresh crash course would very much be appreciated.

---

### Post by northd_tech on 2011-05-04
Hi Rhonda,

Unfortunately, I'm a little confused as to which computer you are working on to get net-connected. :confused:

I'm assuming it's the Desktop computer that you are trying to connect.  I'll give you some commands that need to be run from an Ubuntu terminal (click the "Applications"> at the top of the screen, then "Accessories"> then you will need to scroll down a long way to "Terminal" (there might be 3 or 4 different "Terminal" versions- just pick one- it really doesn't matter which one).

Once you have a Terminal running, here are the commands to enter (on the "Desktop" that you are trying to connect, I believe).  You will likely need a USB thumb/pen drive to copy/paste and save the results to a text file (some of the results will probably be pretty large).  Enter these commands in the Terminal window please (and copy/paste the results to a text file on the USB stick so that you can post them here from a different computer that has a working internet connection):

```
lspci | grep work

sudo lshw -C network

lsmod

lsusb

ifconfig

iwconfig
```

EDIT:  Once we get the necessary info, there is a chance that we can download some .DEB package files to your USB stick that might just "fix" the computer that you can't get connected... but don't quote me on that part... :(

---

### Post by rhondabruce on 2011-05-04
Yes the install is on a desktop. 

blake@blake-OptiPlex-GX270:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
blake@blake-OptiPlex-GX270:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
blake@blake-OptiPlex-GX270:~$ lspci -nn | grep 'asus'
blake@blake-OptiPlex-GX270:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:82:27:ce  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:114056 (114.0 KB)  TX bytes:114056 (114.0 KB)

blake@blake-OptiPlex-GX270:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr off   Fragment thr off
          Power Management on
          
blake@blake-OptiPlex-GX270:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr off   Fragment thr off
          Power Management on
          
blake@blake-OptiPlex-GX270:~$ lsmod
Module                  Size  Used by
bluetooth              65565  0 
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
usb_storage            43946  0 
uas                    17676  0 
rt2870sta             410104  0 
arc4                   12473  2 
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
nls_utf8               12493  1 
isofs                  39571  1 
binfmt_misc            13213  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
nouveau               621970  2 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65184  1 nouveau
drm_kms_helper         40745  1 nouveau
drm                   180037  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13184  1 nouveau
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
video                  18951  1 nouveau
ppdev                  12849  0 
shpchp                 32345  0 
parport_pc             32111  1 
serio_raw              12990  0 
dcdbas                 14054  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
floppy                 60032  0 
e1000                 101089  0 
blake@blake-OptiPlex-GX270:~$ sudo lshw -c network
[sudo] password for blake: 
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 02
       serial: 00:0d:56:82:27:ce
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:18 memory:fcfe0000-fcffffff ioport:df40(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:8
       logical name: wlan0
       serial: bc:ae:c5:7d:8e:5d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.38-8-generic firmware=0.12 link=no multicast=yes wireless=IEEE 802.11bgn
blake@blake-OptiPlex-GX270:~$ lsb_release -d
Description:    Ubuntu 11.04
blake@blake-OptiPlex-GX270:~$ uname -mr
2.6.38-8-generic i686
blake@blake-OptiPlex-GX270:~$ lspci | grep work
blake@blake-OptiPlex-GX270:~$ sudo lshw -c network
[sudo] password for blake: 
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 02
       serial: 00:0d:56:82:27:ce
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:18 memory:fcfe0000-fcffffff ioport:df40(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:8
       logical name: wlan0
       serial: bc:ae:c5:7d:8e:5d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.38-8-generic firmware=0.12 link=no multicast=yes wireless=IEEE 802.11bgn
blake@blake-OptiPlex-GX270:~$ lsmod
Module                  Size  Used by
bluetooth              65565  0 
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
usb_storage            43946  0 
uas                    17676  0 
rt2870sta             410104  0 
arc4                   12473  2 
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
nls_utf8               12493  1 
isofs                  39571  1 
binfmt_misc            13213  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
nouveau               621970  2 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65184  1 nouveau
drm_kms_helper         40745  1 nouveau
drm                   180037  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13184  1 nouveau
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
video                  18951  1 nouveau
ppdev                  12849  0 
shpchp                 32345  0 
parport_pc             32111  1 
serio_raw              12990  0 
dcdbas                 14054  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
floppy                 60032  0 
e1000                 101089  0 
blake@blake-OptiPlex-GX270:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
blake@blake-OptiPlex-GX270:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:82:27:ce  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:114056 (114.0 KB)  TX bytes:114056 (114.0 KB)

blake@blake-OptiPlex-GX270:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr off   Fragment thr off
          Power Management on


I hope this helps.

---

### Post by northd_tech on 2011-05-04
> **rhondabruce said:**
> 
02:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
blake@blake-OptiPlex-GX270:~$** lsusb**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 010: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
blake@blake-OptiPlex-GX270:~$ lspci -nn | **[COLOR=DarkGreen]grep 'asus'[/COLOR]**

blake@blake-OptiPlex-GX270:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr off   Fragment thr off
          Power Management on
          
blake@blake-OptiPlex-GX270:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr off   Fragment thr off
          Power Management on
          
blake@blake-OptiPlex-GX270:~$ lsmod
Module                  Size  Used by
[COLOR=Purple]rt2870sta             410104  0 
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211[/COLOR]

blake@blake-OptiPlex-GX270:~$ sudo lshw -c network
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:8
       logical name: wlan0
       serial: bc:ae:c5:7d:8e:5d
       capabilities: ethernet physical wireless
       configuration: **broadcast=yes [COLOR=Purple]driver=rt2800usb[/COLOR] driverversion=2.6.38-8-generic **firmware=0.12 link=no multicast=yes wireless=IEEE 802.11bgn

blake@blake-OptiPlex-GX270:~$ lsb_release -d
Description:    Ubuntu 11.04

blake@blake-OptiPlex-GX270:~$ uname -mr
2.6.38-8-generic i686


I've whittled the output down to something considerably less. I've highlighted the USB (wireless? Ralink??) modules in [COLOR=Purple]purple[/COLOR].

I haven't worked with those, but it looks like Ralink 2800 to me, and there is a blacklist fix on this thread, I believe (probably post #4):

[http://ubuntuforums.org/showthread.php?t=1700585](http://ubuntuforums.org/showthread.php?t=1700585)

Also, you might want to try your earlier command with a different CaSe:
lspci -nn | [B][COLOR=DarkGreen]grep ASUS
[/COLOR][/B][COLOR=DarkGreen]
[COLOR=Black]Good luck[/COLOR][/COLOR][B][COLOR=DarkGreen], 
[/COLOR][/B][COLOR=Black]ndt[/COLOR][B][COLOR=DarkGreen]
[/COLOR][/B]

---

### Post by rhondabruce on 2011-05-04
This blacklist technique may work. Except I don't know how to. Everything I tried typing into the terminal came back with "no such file or directory". I apologize for the ignorance.

---

### Post by Subharo on 2011-05-18
I'm using Ubuntu 11.04 Natty.  I have an Asus USB-N13.   The minimal "fix" is to merely blacklist rt2800usb in  /etc/modprobe.d/blacklist.conf and reboot.    Thanks, chili555!   :smile:

Here's how, for the complete newbie.  You must be logged in as a user who has Administrative privileges.  The first user created during the Ubuntu install has these privileges.  

In a terminal (in Applications -> Accessories), type: 
[INDENT][FONT=Courier New]sudo gedit  /etc/modprobe.d/blacklist.conf[/FONT]
[/INDENT]Provide your user's password when asked.  Gedit should now launch and open the file.  At the end of the file, add the line:
[INDENT][FONT=Courier New]blacklist rt2800usb[/FONT]
[/INDENT]save, exit, reboot!

---

### Post by willz06jw on 2011-06-17
Adding this blacklist entry worked for me too.

Why do I have to add this blacklist entry though?  Is this a bug that needs to be reported?

Thanks,
Will

---

### Post by Ghoulish on 2011-07-01
> **Subharo said:**
> I'm using Ubuntu 11.04 Natty.  I have an Asus USB-N13.   The minimal "fix" is to merely blacklist rt2800usb in  /etc/modprobe.d/blacklist.conf and reboot.    Thanks, chili555!   :smile:

Here's how, for the complete newbie.  You must be logged in as a user who has Administrative privileges.  The first user created during the Ubuntu install has these privileges.  

In a terminal (in Applications -> Accessories), type:[INDENT][FONT=Courier New]sudo gedit  /etc/modprobe.d/blacklist.conf[/FONT]
[/INDENT]Provide your user's password when asked.  Gedit should now launch and open the file.  At the end of the file, add the line:[INDENT][FONT=Courier New]blacklist rt2800usb[/FONT]
[/INDENT]save, exit, reboot!

I LOVE you! ....DAYS spent working on this as a complete linux newbie and your solution worked in like 10 seconds. Thank you SO much.

---

### Post by blwuee on 2011-09-21
> **Ghoulish said:**
> I LOVE you! ....DAYS spent working on this as a complete linux newbie and your solution worked in like 10 seconds. Thank you SO much.

thank's peeps. i too spent days trying to other methods. who knew so little was required, after going through so much. i love you chilli! thanks heaps. 

you'd think that's i'd be surfing the internet like mad now, but no! i can finally have a good night's sleep.

---

### Post by jwnuttall on 2011-12-22
I am also having problems getting the same usb network adaptor working in Natty.  I have tried blacklisting it to no avail.  It doesn't even seem to be recognizing that I have a network adaptor.  I am fairly new to Ubuntu, but here is the output from the request from the second post:
john@john-desktop:~$ lspci | grep work
john@john-desktop:~$ 
john@john-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:01:6c:b8:2d:e1
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.5 latency=32 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100Mbit/s
       resources: irq:19 ioport:e000(size=256) memory:e4122000-e4122fff memory:60000000-6001ffff
john@john-desktop:~$ 
john@john-desktop:~$ lsmod
Module                  Size  Used by
snd_hrtimer            12681  1 
binfmt_misc            17374  1 
snd_ens1371            24854  2 
gameport               19468  1 snd_ens1371
snd_ac97_codec        106029  1 snd_ens1371
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                81557  2 snd_ens1371,snd_ac97_codec
snd_seq_midi           13170  0 
snd_rawmidi            25327  2 snd_ens1371,snd_seq_midi
radeon                946355  3 
snd_seq_midi_event     14475  1 snd_seq_midi
ttm                    65896  1 radeon
snd_seq                51702  3 snd_seq_midi,snd_seq_midi_event
ppdev                  12869  0 
drm_kms_helper         41670  1 radeon
snd_timer              29140  3 snd_hrtimer,snd_pcm,snd_seq
drm                   192836  5 radeon,ttm,drm_kms_helper
snd_seq_device         14160  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13204  1 radeon
snd                    56136  12 snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32578  1 
shpchp                 32421  0 
i2c_sis96x             12743  0 
psmouse                65817  0 
soundcore              12600  1 snd
lp                     13412  0 
sis_agp                13158  1 
snd_page_alloc         14108  1 snd_pcm
serio_raw              13094  0 
parport                41188  3 ppdev,parport_pc,lp
sis900                 26830  0 
floppy                 60478  0 
john@john-desktop:~$ 
john@john-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
john@john-desktop:~$ 
john@john-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:6c:b8:2d:e1  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:6cff:feb8:2de1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29530719 (29.5 MB)  TX bytes:4601474 (4.6 MB)
          Interrupt:19 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1708 (1.7 KB)  TX bytes:1708 (1.7 KB)

john@john-desktop:~$ 
john@john-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


Please help!  Thanks.

---

### Post by chili555 on 2011-12-22
Does this bring your wireless to life? If so, we can make it permanent. If not, post any errors or warnings:```
sudo modprobe rt2870sta
```

---

### Post by jwnuttall on 2011-12-25
No.  Unfortunately it gives me the following error:

FATAL: Module rt2870sta not found.

Sorry about the late response.  I thought I would get an email when someone responded to my reply.

---

### Post by jwnuttall on 2011-12-25
I tried following the instructions on this website to build and install the driver: [http://xlcwu.wordpress.com/2010/07/09/build-rt3070-kernel-module-on-ubuntu-10-04-lucid-lynx/](http://xlcwu.wordpress.com/2010/07/09/build-rt3070-kernel-module-on-ubuntu-10-04-lucid-lynx/)

but when I entered "sudo modprobe 2870rta" in terminal, it still came up with "FATAL: Module rt2870sta not found."module not found.  It seems that it is not being added to /proc/modules file.  Is there a way to get it added there?  Thanks.

---

### Post by chili555 on 2011-12-28
Now I'm sorry for my delayed response. Holidays and out-of-town guests...

We wonder what is driving your device! If you are running 11.10, the newer driver is rt2800usb. Does this work?```
sudo modprobe rt2800usb
```If so, you'll need to reverse your blacklist. If not, we'll troubleshoot.

---

### Post by jwnuttall on 2011-12-29
It does look like rt2800usb was listed in lsmod, but when I tried modprobe like you suggested, nothing changed.  I then decided to re-install.  I had been using Dream Studio 11.04 and decided to get rid of that and install normal Ubuntu 11.10.  My network adaptor now works without any problems.  I didn't have to do anything to install it at all!  I guess it is just a bug in Dream Studio.  Thanks for your help.

---

