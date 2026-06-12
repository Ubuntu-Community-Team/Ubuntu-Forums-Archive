---
title: "Compiz Crashing"
date: 2009-06-26
forum: Multimedia Software
---

### Post by WinterWeaver on 2009-06-26
I've never had this problem before. It started with my new Laptop, on which I installed Jaunty.

It's an acer aspire 7530, with a NVidia GeForce 9100M G video card.

What happens is. I can start up compiz and it runs for a while, with all the effects etc. After a couple of minutes however, I would be doing something, and suddenly the screen freezes, music still playing in the background. Sometimes, graphics glitches will appear on screen which looks like the windows were moving around but didn't redraw properly.

The only way to get back is to ALT+SyncRq + K.

Currently I'm running with metacity, but would love to have compiz working again, as I've been happily using it for 2 years now (maybe a bit less :P ).

lspci output:
```
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 SATA controller: nVidia Corporation Device 0ad5 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:16.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9100M G (rev a2)
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
```

thx,

WW

---

### Post by milesnapue on 2009-06-26
Try this [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)
 
Great script.

---

### Post by WinterWeaver on 2009-06-27
Thanks milesnapue,

Scritpt is passing as normal... aeverything is ok :(

```
./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 9100M G (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


```

---

### Post by WinterWeaver on 2009-06-27
Touch Wood, my compiz seems to be working now.

It may be one of 3 things.

1. I completely removed Compiz and reinstalled it
2. I enabled compiz via Alt+F2 >> compiz --replace   , instead of enabling it via the Visual Effects tab in the Appearance Preferences.
3. I disabled mouse polling. my reason for this is that every time just before compiz freaked out on me, the mouse started to stutter, i thought that there may be some bug there.

Too short period to say if any of these actually worked... I'm hoping it wont crash again :P

---

### Post by WinterWeaver on 2009-06-27
Boom crash... >.< ... again.

---

### Post by WinterWeaver on 2009-08-03
Noticed a couple of things that cause the Freeze.


[LIST]
[*]If the terminal has a transparent background, and I'm hard at work, quickly moving or resizing it.
[*]Certain Metacity or GTK themes also causes it to freeze when I click on the Empathy Status bar, to change my status.
[/LIST]
(btw... tried Kubuntu, but freezes are even more common there.)

So I have now disabled the terminal transparent background. I also use a gtk and metacity theme which does not freeze when I'm changing my empathy status. The Freezing is now few and far between, but unfortunately they are not eliminated.

Does someone have any way for me to try and diagnose the problem?

Thanks,

WW

---

### Post by tylerisfat on 2009-10-27
> **WinterWeaver said:**
> Noticed a couple of things that cause the Freeze.


[LIST]
[*]If the terminal has a transparent background, and I'm hard at work, quickly moving or resizing it.
[*]Certain Metacity or GTK themes also causes it to freeze when I click on the Empathy Status bar, to change my status.
[/LIST]
(btw... tried Kubuntu, but freezes are even more common there.)

So I have now disabled the terminal transparent background. I also use a gtk and metacity theme which does not freeze when I'm changing my empathy status. The Freezing is now few and far between, but unfortunately they are not eliminated.

Does someone have any way for me to try and diagnose the problem?

Thanks,

WW


I'm having a problem very much like this. unfortunately im on a lappy, without the needed keys to restart X. Full reboots the only thing i can do. Dang it.


Anyone got a good description of this so i can ask google more questions?

---

