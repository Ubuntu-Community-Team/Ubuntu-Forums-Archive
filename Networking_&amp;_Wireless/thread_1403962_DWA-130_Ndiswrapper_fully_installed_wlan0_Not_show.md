---
title: "DWA-130 Ndiswrapper fully installed wlan0 Not showing up"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by WickedShadow on 2010-02-10
Alright so im a newbie to linux and ubuntu and i follow all instructions on how to install ndiswrapper and then installed my driver also i dont know if relevent but when installed it said "unable to tell if hardware is present" but anyway its all installed and i go to the network manager go under wireless but there is no "wlan0" infact there is nothing at all. Any ideas?

My Setup:
Dual-Booted Linux + XP
2.6 amd proccessor
ubuntu 9.10
2.5 gigs of ram
custom built.

My adapter is compatible yet no results please help.

Best Regards,
WickedShadow

---

### Post by bkratz on 2010-02-10
Do you know which version of the DWA-130 you have? The label on the back will say something like DWA130-A1 (mine). There are four versions available. Also you might want to go to the terminal ( Applications//Accessories//Terminal) and copy/paste the output of 

sudo lshw -C network
(that is a little L in lshw)
back here.  The sudo will force you to put in your password which will not be echoed back to you, just press enter after putting it in.

---

### Post by WickedShadow on 2010-02-10
I have the same as you and i will do that and reply back.

---

### Post by WickedShadow on 2010-02-10
Here is the output:
 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: eth1
       version: 10
       serial: 00:02:44:81:f2:9a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:18 ioport:ac00(size=256) memory:fe9fe000-fe9fe0ff
  *-network
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 19
       serial: 00:01:6c:cd:e7:7b
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:fe4fc000-fe4fffff ioport:7c00(size=256) memory:fe300000-fe31ffff(prefetchable)

---

### Post by bkratz on 2010-02-10
How about 

lsusb

 with the device plugged in.  All I see are two ethernet controllers??

---

### Post by bkratz on 2010-02-10
I'll subscribe to the thread and check back tomorrow, for now I have to sleep.  If you put in DWA-130 in the search box at the top of the screen you will find several threads.

Here is one where I gave directions on installation, but never heard back. Unfortunately, although I got the DWA-130 to work reliably in 8.10,9.04 and the not yet released 10.04, I never really did get it to work well in 9.10 with any type of encryption and eventually went back to 9.04 until 10.04 is released. 

[http://ubuntuforums.org/showthread.php?t=1346247&highlight=dwa-130](http://ubuntuforums.org/showthread.php?t=1346247&highlight=dwa-130)

---

### Post by WickedShadow on 2010-02-10
Bus 002 Device 002: ID 046d:c049 Logitech, Inc. G5 Laser Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 07d1:3b11 D-Link System Wireless N Adapter DWA-130
Bus 001 Device 002: ID 0bc2:2100 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 here is the USB outpu

---

### Post by WickedShadow on 2010-02-10
*cough* anyone else?

---

### Post by WickedShadow on 2010-02-11
this is still unsolved

---

### Post by bkratz on 2010-02-11
> **WickedShadow said:**
> this is still unsolved

When you installed the drivers did you do it similar to how I described in the other thread, or how did you do it? Did it ever say hardware present?  How did you determine in post 1 that it was "installed".

---

### Post by WickedShadow on 2010-02-11
> **bkratz said:**
> When you installed the drivers did you do it similar to how I described in the other thread, or how did you do it? Did it ever say hardware present?  How did you determine in post 1 that it was "installed".

1. I installed ndiswrapper and its graphical interface then installed the driver using the proper .inf or whatever it askes for.
2. Yes kinda, It say when i startup or run "windows wirless drivers" it say "Unable to tell if hardware is present" but then it says under the name of the .inf that its present and when i look at it after i unplug it is notices its gone and then says no so that "seems" to be functioning.

---

### Post by bkratz on 2010-02-12
> **WickedShadow said:**
> 1. I installed ndiswrapper and its graphical interface then installed the driver using the proper .inf or whatever it askes for.
2. Yes kinda, It say when i startup or run "windows wirless drivers" it say "Unable to tell if hardware is present" but then it says under the name of the .inf that its present and when i look at it after i unplug it is notices its gone and then says no so that "seems" to be functioning.

Hopefully I attached a picture. Won't be sure until I actually send this, but do you see this screen when accessing the ndisgtk windows wireless in System>>Administration>>Windows wireless drivers menu?
If not, were the names of the .inf and .sys files that you linked to the same as in my demo (other link)? If not, I would say you have the wrong files, I can email the working drivers (right from my system) to you if need be just PM me (don't put your email address here!).

---

### Post by WickedShadow on 2010-02-19
Yes i do and sorry for late response.

---

### Post by bkratz on 2010-02-19
> **WickedShadow said:**
> Yes i do and sorry for late response.

I think it is time to go to the terminal (Applications>>Accessories>>Terminal) and type in

```
sudo lshw -C network
```

(that is LSHW in lowercase and C in upper), it will require your password which will not be echoed to you, press enter when password is typed in.  Copy/paste the output back here.

```
  *-network               
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: eth0
       version: 10
       serial: 00:01:80:65:aa:69
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.75 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=MII speed=100MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 06:16:fd:19:95:2c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1b:11:f3:3b:fb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netmw245 driverversion=1.53+Marvell,11/27/2006,1.0.4.9 link=no multicast=yes wireless=IEEE 802.11g


```

This is what mine looks like, note that I am using 9.04 so it shows that ndiswrapper is version 1.53

---

### Post by WickedShadow on 2010-02-21
Here is the output: (Don't know if this applies but it is USB)
```
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: eth1
       version: 10
       serial: 00:02:44:81:f2:9a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:18 ioport:ac00(size=256) memory:fe9fe000-fe9fe0ff
  *-network
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 19
       serial: 00:01:6c:cd:e7:7b
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:fe4fc000-fe4fffff ioport:7c00(size=256) memory:fe300000-fe31ffff(prefetchable)

```

---

### Post by bkratz on 2010-02-21
Sorry for the stupid question, but did you have it plugged in when you ran this, it doesn't seem to be recognized.  See the wlan0 section in mine (which disappears when not plugged in).

Could you please post

lsmod  (LSMOD in lowercase)

---

### Post by WickedShadow on 2010-02-21
Yes it was plugged in (not a stupid question), and will do.

---

### Post by WickedShadow on 2010-02-21
Here is the output:

```
owner@ubuntu:~$ lsmod
Module                  Size  Used by
isofs                  36424  0 
udf                    88136  1 
crc_itu_t               2336  1 udf
binfmt_misc            10220  1 
snd_intel8x0           36872  2 
snd_ac97_codec        125720  1 snd_intel8x0
ac97_bus                2176  1 snd_ac97_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
iptable_filter          3872  0 
ppdev                   8232  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
snd_seq_dummy           3460  0 
nvidia              10316904  36 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
ndiswrapper           245280  0 
k8temp                  5504  0 
amd64_edac_mod         26688  0 
edac_core              48876  3 amd64_edac_mod
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
parport_pc             37352  1 
lp                     11908  0 
parport                40528  3 ppdev,parport_pc,lp
i2c_nforce2             8168  0 
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_intel8x0,snd_pcm
usb_storage            66016  1 
usbhid                 43968  0 
8139too                27360  0 
sky2                   55556  0 
8139cp                 23200  0 
mii                     6368  2 8139too,8139cp
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
floppy                 65192  0 
forcedeth              61292  0 
```

---

### Post by bkratz on 2010-02-21
does your output of

ndiswrapper -l    (that is a lowercase L)


look like mine. It shows the driver used and if there are alternates

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

netmw245 : driver installed
	device (07D1:3B11) present



By the way here is an excellent troubleshooting guide for ndiswrapper


[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

### Post by WickedShadow on 2010-03-03
Again sorry for the late response here is the output:
```
owner@ubuntu:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/bloacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist line 6: ignoring bad line starting with 'blaoclist'
WARNING: /etc/modprobe.d/blacklist line 8: ignoring bad line starting with 'bloacklist'
netmw245 : driver installed
	device (07D1:3B11) present


```

---

### Post by fermulator on 2010-11-21
see the post here; [http://gutsywww.ubuntuforums.org/showthread.php?t=1425697&page=3](http://gutsywww.ubuntuforums.org/showthread.php?t=1425697&page=3)

it works out of the box now, ndiswrapper not required for RevE

---

