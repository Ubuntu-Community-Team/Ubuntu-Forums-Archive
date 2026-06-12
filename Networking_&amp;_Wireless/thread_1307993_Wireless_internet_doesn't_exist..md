---
title: "Wireless internet doesn't exist."
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by jfinner1 on 2009-10-31
Yes, another one. I can't get my wireless internet to work after upgrading to 9.10. Here's my outputs. I'm hoping it's an easy fix. Thanks guys. Someday I'll actually figure out how to... well, figure this stuff out...

00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
01:05.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83)
01:0b.0 CardBus bridge [0607]: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support [1179:0617] (rev 33)

  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=28 mingnt=10
       resources: memory:cfff0000-cfffffff
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 83
       serial: 00:0e:7b:cf:c0:95
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.1.107 latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:11 memory:cffef000-cffeffff ioport:cf00(size=64)

---

### Post by chili555 on 2009-10-31
Please see posts #5 and #8 here: [http://ubuntuforums.org/showthread.php?t=1305812&highlight=AR2413](http://ubuntuforums.org/showthread.php?t=1305812&highlight=AR2413)

---

### Post by addtoqueue on 2009-11-01
> **chili555 said:**
> Please see posts #5 and #8 here: [http://ubuntuforums.org/showthread.php?t=1305812&highlight=AR2413](http://ubuntuforums.org/showthread.php?t=1305812&highlight=AR2413)

My laptop has that Atheros card and posts #5 and #8 did not solve the problem.

---

### Post by jfinner1 on 2009-11-01
Yup, tried it, no change. Sorry. Now what?

---

### Post by chili555 on 2009-11-02
Please let me see the results of these terminal commands:```
sudo modprobe ath5k
sudo ifconfig wlan0 up
iwconfig
```Thanks.

Some of these may produce no output, meaning the command was accepted and executed with no errors or warnings. That's fine.

---

### Post by jfinner1 on 2009-11-02
No response from the first two commands. The third looks a bit discouraging to me...

jfinner1@Thor:~$ sudo modprobe ath5k
jfinner1@Thor:~$ sudo ifconfig wlan0 up
jfinner1@Thor:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by cybergalvez on 2009-11-02
it looks like the ath5k driver works, make sure its not being blacklisted (look in the files in /etc/modprobe.d folder) and then try adding ath5k to the end of your /etc/modules file.  once you reboot network manager should be able to see your Atheros card

---

### Post by jfinner1 on 2009-11-02
I hate to ask this, especially since I've been a Ubuntu user for over a year now... But can you put that into dummy language for me? I'm not sure I'll ever truly understand terminal commands...

---

### Post by jfinner1 on 2009-11-03
OMG I figured it outI got into the file by typing"gksudo gedit /etc/modules" then typed ath5k at the very bottom, hoping it wouldn't break anything. And it worked! Thank You!!:grin::grin::grin::grin::grin:

---

