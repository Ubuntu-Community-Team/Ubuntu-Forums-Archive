---
title: "in dire need of help installing ndiswrapper!"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by dillingerzombie on 2009-07-27
okay so i am absolute just-installed-ubuntu-yesterday noob at all of this, so if someone is willing to walk me through the process of getting wireless internet on this laptop, i will be eternally grateful.

so i just installed ubuntu 9.04 onto my family's old hp-compaq presario c300, and i've been trying to get internet access from my linksys452 router.

i've been following the instructions from this site:
[http://www.linlap.com/wiki/HP-Compaq+Presario+C300](http://www.linlap.com/wiki/HP-Compaq+Presario+C300)
so i installed ndiswrapper-utils-1.9 and tried opening it using
[INDENT]sudo apt-get install ndiswrapper-utils-1.9[/INDENT]
including several variants, but always ended up getting the same results, this message:
[INDENT]E: Couldn't find package ndsiwrapper-utils-1.9[/INDENT]

i have the file downloaded onto the desktop if that has anything to do with not being able to find the file... and i can give more information about the situation as needed, of course.

thanks in advance for any help you can offer me! :D

---

### Post by dillingerzombie on 2009-07-27
well seeing as how i'm already off the first page, i've gotta bump this :o

---

### Post by wojox on 2009-07-27
Have you looked here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by alleycatuk on 2009-07-27
Hi, I'm about a day ahead of you - installed on Saturday and spent Sunday pulling my hair out. I now have a WPA2 wireless connection on my desktop.
A few bits I've figured out which may help you:
If you don't have any internet, take this off your repositories... go to System - Administration - Synaptic package manager then do Settings - Repositories and untick anything that looks at all like it's internet (which I think is most things!)
If you have the ubuntu cd, you should be able to install from there:
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

Hope that does it for you. I'm struggling on getting the wireless to start automatically but at least I have a manual connection now.
Best of luck

---

### Post by dillingerzombie on 2009-07-27
ah thank you both so much!
i'm pretty sure i've successfully installed ndiswrapper...
but now i don't know what to do next.

---

### Post by superprash2003 on 2009-07-28
post output of the following
1)lshw -C network
2)iwconfig
3)sudo iwlist scanning

---

### Post by dillingerzombie on 2009-07-28
> **superprash2003 said:**
> post output of the following
1)lshw -C network
2)iwconfig
3)sudo iwlist scanning

here's what i got...
```

1) -----------------------------------------------------------
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:45:fd:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:f0:b6:3c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 26:c2:3b:e5:a7:0d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

2) -----------------------------------------------------------
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

3) -----------------------------------------------------------
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

```

---

### Post by superprash2003 on 2009-07-29
[http://ubuntuforums.org/showthread.php?t=1225208](http://ubuntuforums.org/showthread.php?t=1225208) .. check out post no 6

---

