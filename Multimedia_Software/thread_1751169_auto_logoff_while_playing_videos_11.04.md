---
title: "auto logoff while playing videos 11.04"
date: 2011-05-06
forum: Multimedia Software
---

### Post by dineshs on 2011-05-06
I installed ubuntu 11.04 on my desktop PC .While trying to play videos using smplayer the screen goes blank then the login screen appears.Tried vlc with no luck.Working fine on office PC
Kindly help.

---

### Post by dineshs on 2011-05-09
please help

---

### Post by dineshs on 2011-05-11
bump
lspci says
```
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0f.0 IDE interface: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 70)
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)
02:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
02:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
```

---

### Post by dineshs on 2011-05-13
Pl help

---

### Post by leojan on 2011-05-15
am having the same problem please help

---

### Post by dineshs on 2011-05-18
bump

---

### Post by Apostolique on 2011-05-22
No one found any solution for this yet?

---

### Post by nike984 on 2011-05-22
[http://askubuntu.com/questions/43790/system-logs-out-on-video-playing-in-full-screen](http://askubuntu.com/questions/43790/system-logs-out-on-video-playing-in-full-screen)

Please change video drivers to x11 
and test it again

---

### Post by Apostolique on 2011-05-22
Looks like it's done the job. Thanks a lot!
> 
After upgrading to Ubuntu 11.04, a strange behaviour i am getting on video playing full screen in Totem, vlc, smplayer, xine player. The system logs out every time i play a video, almost all video formats i have tried.

I have resolved this problem, changing video drivers of the said player to x11,

[LIST=1]
[*]smplayer: Options --> Preferances--> Video --> Output Driver --> x11(slow)
[*]vlc: Tools --> Preferences --> Video --> UNCHECKED Accelerated Video Output
[/LIST]
Now the Videos are playing on FULL-SCREEN without logging off.

As of totem movie player, couldn't find this option, how to change.

However, this seems odd, that i have not noticed this thing in previous versions of Ubuntu i have used.


---

### Post by dineshs on 2011-05-23
Many many thanks to nike984.

---

### Post by beew on 2011-05-23
> **nike984 said:**
> [http://askubuntu.com/questions/43790/system-logs-out-on-video-playing-in-full-screen](http://askubuntu.com/questions/43790/system-logs-out-on-video-playing-in-full-screen)

Please change video drivers to x11 
and test it again

This is not really a solution as x11 performs poorly.

---

### Post by raxhonp on 2011-06-15
That's a known bug in xserver-xorg-video-openchrome. A fix is available, but I didn't test it myself and don't know if that would solve your particular problem. See [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/760743](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/760743).

---

### Post by dineshs on 2011-06-15
beew was right
I tried postcount #11 in the link suggested by raxhonp (Thanks) .It seems OK.

---

