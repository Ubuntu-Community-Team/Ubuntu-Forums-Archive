---
title: "1 mb/s with wireless"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by Burky on 2009-12-24
I have Ubuntu Karmic Koala and I'm using a the Netgear WG111v3 USB wireless card. I usually get 11mb/s with this on Ubuntu and about 54mb/s on Windows. Lately I've been getting 1 mb/s on Ubuntu and still 54 mb/s on Windows. Anyone know what caused this and/or how to fix this?

---

### Post by darco on 2009-12-24
run iwconfig in a terminal....look for the "bit rate" as it may show 1mb. If so, then run ```
sudo iwconfig wlan0 rate 54M
```


darco

---

### Post by elliotbeken on 2009-12-24
hi there, 

to me about 1mb/s sounds ok for wireless. as the hardware never runs at full speed that the manufacture says it will.

have to moved location (moved the router or the pc)?

---

### Post by Burky on 2009-12-24
> **elliotbeken said:**
> hi there, 

to me about 1mb/s sounds ok for wireless. as the hardware never runs at full speed that the manufacture says it will.

have to moved location (moved the router or the pc)?

The computer is dual booted with Ubuntu and Windows 7. I get 54 mb/s on windows and before I got 11 mb/s on Ubuntu. Nothing changed as far as routers or location and now I get 1 mb/s on Ubuntu. It's something having to do with Ubuntu.

Darco, I'm gonna try that. I'll post the results here.

---

### Post by tripolitan on 2009-12-24
What are you using to measure your WiFi speed?
A shot in the dark; Assuming that your PC is the only PC on your wifi network (if not, wifi signal is split between nodes)

sudo /etc/init.d/networking restart

check the speed after that.

---

### Post by Burky on 2009-12-24
> **darco said:**
> run iwconfig in a terminal....look for the "bit rate" as it may show 1mb. If so, then run ```
sudo iwconfig wlan0 rate 54M
```


darco

I tried that. Now it says 54 mb/s... cool. But it's still too slow to even connect to pidgin?

EDIT: I restarted the computer and it's back to it's normal speeds, thanks a lot Darko!

---

### Post by darco on 2009-12-24
cool!...you should mark this thread as "solved" to help others.
Go to Thread tools.....


darco

---

### Post by Burky on 2009-12-24
Now that we're on the topic why does Windows say it's around 48-54 mb/s (it changes a lot) and Ubuntu always says 11 mb/s?

---

### Post by darco on 2009-12-24
post the output of 
```
lspci
```

---

### Post by Burky on 2009-12-24
```
david@david-desktop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02
```

---

### Post by darco on 2009-12-24
post output of iwconfig

---

### Post by Burky on 2009-12-24
```
david@david-desktop:~$ sudo iwconfig
[sudo] password for david: 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"NETGEAR-2.4-G"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:B2:AC:6E:67   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

```

---

### Post by darco on 2009-12-24
yes its strange that the bit rate reverted back to 11mb. I cant see what your wireless card is though but it must be a "G" as your windows shows 54mbs.
I would re run the command to boost it back up and see if it changes only after a reboot or while your are still logged in.


darco

---

### Post by Burky on 2009-12-24
I ran ```
sudo iwconfig wlan0 rate 54M
``` then it says 54 mb/s while logged in, as soon as i reboot it goes back to 11 mb/s.

---

### Post by darco on 2009-12-24
I would google your wl card for any known bugs. For now at least you have a work around :)


darco

---

### Post by Burky on 2009-12-24
Yep i sure do, thanks

---

### Post by jllb on 2010-03-16
Same issue here. I don't think the problem should be marked as solved since it reappears when rebooting the computer.

---

### Post by nitstorm on 2010-03-16
> **darco said:**
> run iwconfig in a terminal....look for the "bit rate" as it may show 1mb. If so, then run ```
sudo iwconfig wlan0 rate 54M
```
darco


Tried doing this on my home PC which is a wired connection, i mean i typed in ifconfig but i found no such thing as bit rate mentioned, how can i speeds in ubuntu like i used to on windows?

---

