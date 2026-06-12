---
title: "Sound broken after update!"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by richgood on 2007-09-03
Morning,

After my update this morning my sound card does'nt seem to be detected anymore.

I'm running Ubuntu Feisty Fawn (2.6.20) on a desktop machine and had my sound working happily previously.

Now my volume control on the desktop panel says: 
no Volume control GStreamer Plugins and/or device found

here is my output on lspci:
```
richard@Richard:~/Desktop/Downloads/realtek-linux-audiopack-4.06b$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 0e)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
```

Here is my output on aplay -L
```
aplay: device_list:222: no soundcards found...

```

Also when I try to run alsaconf I get command not found.

As I said I had it working previously and have all the neccessary alsa-base, alsa-utils, libasound packages installed.

Any ideas?

thanks,
Richard

---

### Post by richgood on 2007-09-03
Followed a post a few down - recompiled alsa restarted and its works.

Apologies for hassling before searching the forum!

---

