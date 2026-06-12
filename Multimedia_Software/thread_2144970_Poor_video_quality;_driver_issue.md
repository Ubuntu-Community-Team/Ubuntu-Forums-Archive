---
title: "Poor video quality; driver issue?"
date: 2013-05-13
forum: Multimedia Software
---

### Post by lisistaan on 2013-05-13
I have been a Windows user all my life but got bored of it. Decided to give Ubuntu a go. Downloaded and installed Ubuntu 13.4 yesterday and so far am loving it. But one thing I've noticed is that graphics quality does not seem to be as good as it was for Windows 7 on the same laptop. (Lenovo Z580 with Intel HD 4000 integrated graphics card) The colors don't seem to "pop" and appear a bit washed out and text will give me a headache sometimes because it seems hard to read. But the main issue is video quality, I've downloaded VLC and have tried watching videos but the quality is very poor. The colors are all washed out and "bland" is the best way I can word it. Also if there's too much happening on screen the video becomes glitchy and choppy. It doesn't seem like the computer can handle it but before I could view HD movies in perfect quality. I was just wondering if this could be a graphics driver issue that could be fixed? I've tried searching the internet but the results seem confusing. Was hoping someone here could help me out.

---

### Post by Bucky Ball on 2013-05-13
Do an update (use Update Manager) then have a look in Additional Drivers. Anything there for your graphics card?

You could also open a terminal (Applications>Accessories>Terminal from memory) and paste this in:

```
lspci
```

Hit return and post the output here. That will tell us what card you have in there and give a ton of info about your machine.

---

### Post by carl4926 on 2013-05-13
It shouldn't really be a problem
I can tell any difference on my Intel Lenovo or other machines. Though the drivers for Intel are not the same as in windows... don't ask, it a stupid and complicated story of licencing. 
I actually think the font rendering is better now in Linux than in Windows.

You could post the result of this

```
lspci -nnk
```we will see most of your hardware and drivers from that. Please put it in code tags

---

### Post by lisistaan on 2013-05-13
Firstly, thank you both for replying.

I did the update and went to Additional Drivers, it says that I have no proprietary in use and there's nothing there in the list. I've now tried various HD videos and youtube and I get the same issue, colors seem like they have low contrast and are not really vivid at all. If something fast happens the video gets choppy and a random thick black line will flash across the video. 

```
 lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
    Subsystem: Lenovo Device [17aa:3977]
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Lenovo Device [17aa:3977]
    Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Kernel driver in use: mei
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
    Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 [8086:1e14] (rev c4)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2200 [8086:0891] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2200 BGN [8086:4222]
    Kernel driver in use: iwlwifi


```

---

### Post by carl4926 on 2013-05-14
This looks normal
```
[COLOR=#000000][FONT=Ubuntu Mono]00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)[/FONT][/COLOR]
    Subsystem: Lenovo Device [17aa:3977] [COLOR=#000000][FONT=Ubuntu Mono]    Kernel driver in use: i915[/FONT][/COLOR]
```

Youtube
I have read of some issues recently in youtube in other forums where there has been a need to disable HW acceleration in the flash settings

Is the trouble only with HD
And by HD what do you mean spec wise?

---

### Post by lisistaan on 2013-05-14
No it's in VLC too not just youtube. By HD I mean 720p or 1080p MP4 files but it's not just those. Any video gets choppy and random lines and pixelation happens if something fast or sudden happens on screen.

---

### Post by carl4926 on 2013-05-14
I don't really watch much video, but some from BBC is HD. It always seems OK though.

So you installed the restricted extras? I guess.

VLC should be fine, I don't use it myself as I prefer smplayer as it remembers where you left off.

Not sure what else to suggest.

---

### Post by CatKiller on 2013-05-14
This may be a stupid question, but are you running at native resolution?

---

### Post by lisistaan on 2013-05-14
I am, yes. At least I'm using the one Ubuntu chose as default: 1366X768 (16:9). My only other options are 1360X768 or a 4:3 display.

---

### Post by CatKiller on 2013-05-14
> **lisistaan said:**
> I am, yes. At least I'm using the one Ubuntu chose as default: 1366X768 (16:9).

One thing does not mean the same as the other. Sounds like a realistic resolution, though. You might find that text becomes easier to read if you fiddle with the sub-pixel rendering settings.

---

