---
title: "XRandR is showing the wrong Maximum resolution in Ubuntu 8.10"
date: 2008-12-01
forum: Multimedia Software
---

### Post by isleshocky77 on 2008-12-01
I've been running Kubuntu 8.04 - KDE 4.1 for quite some time now. I'm thinking about switching over to gnome so I figured I'd test it out with the 8.10 release.  

However, now I can't my dual monitor setup working.  I have a Compaq Presario v2335us with "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)". I also have a Gateway FPD2185W 21" HD monitor which I use as second screen to the laptop. Using the "Screen Resolution" app I was able to set it up as a second location in the correct location. But it will only let me make it 1600x1024.  It's an HD monitor and should be 1680x1050.

When I do an output on Xrandr I see that it states the maximum of the monitor is 2624 x 1024.  How can I get this fixed?

Output of Xrandr
```
Screen 0: minimum 320 x 200, current 2624 x 1024, maximum 2624 x 1024
VGA connected 1600x1024+0+0 (normal left inverted right x axis y axis) 450mm x 280mm
   1600x1024      60.2* 
   1280x1024      75.0     60.0     60.0  
   1440x900       75.0     59.9     60.0  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     75.0     70.0     70.0     60.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
LVDS connected 1024x768+1600+184 (normal left inverted right x axis y axis) 305mm x 183mm
   1280x768       60.0 +
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)

```

Output of lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

```

Thanks for any help.

---

