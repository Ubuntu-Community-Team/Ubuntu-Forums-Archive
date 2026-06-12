---
title: "Problem with ATI Mobility X300 and Dual VIew (1680x1050)"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by MarkSchmidt on 2008-02-25
Hi there!

I have got a Dell Inspiron with a Radeon X300 Mobility and an external monitor from VIewsonic (VA2012W).
Some time ago I installed a new ATI driver - the first one with the 1680-external-monitor-dualhead-problem. Since I did not have the time then to switch back, I just unplugged my external monitor. Now I read that the new one does not have this problem anymore - so I hoped. But I can just not get my external monitor to work with fglrx with 1680x1050 - the only resolution it gives me is 1024*768.

I tried a BigDesktop as well as now dual head - always I see the same in the Xorg-Log:

> (II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: XXX  Model: 3  Serial#: 0
(II) fglrx(0): Year: 1990  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 40  vert.: 30
(II) fglrx(0): Gamma: 1.00
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; Non RGB Multicolor Display
(II) fglrx(0): First detailed timing not preferred mode in violation of standard!(II) fglrx(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
(II) fglrx(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff006318030000000000
(II) fglrx(0): 	0000010300281e00f000000000000000
(II) fglrx(0): 	00000021080031404540614000000000
(II) fglrx(0): 	00000000000000000000000000000000
(II) fglrx(0): 	00000000000000000000000000000000
(II) fglrx(0): 	00000000000000000000000000000000
(II) fglrx(0): 	00000000000000000000000000000000
(II) fglrx(0): 	0000000000000000000000000000008e
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Connected Display2: LCD on internal LVDS [lvds]
(II) fglrx(0):  Display2: No EDID information from DDC.
(II) fglrx(0):  Display2: Failed to get EDID information. 
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Secondary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  5 power states available:
(II) fglrx(0):   1. 297/216MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 100/122MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   3. 105/182MHz @ 60Hz [low voltage, enable sleep, thermal diode mode]
(II) fglrx(0):   4. 209/182MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   5. 209/182MHz @ 60Hz [low voltage, enable sleep, thermal diode mode]
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled

So, can I hack this somehow to get it to know that my monitor DOES support 1680x1050? It seems that even if I have the configuration right, this one does not know my monitor...
btw, I have Kubuntu Gutsy running.

I hope anyone can help me - many thanks!

Mark

---

### Post by MarkSchmidt on 2008-03-08
Hm, has no one any idea?

---

### Post by yanbee on 2008-03-24
Good News!!

I have the same problem, my monitor is a Samsung SyncMaster 223bw and my graphics card is an ATI X1950 Pro. I couldn't get 1680x1050 resolution, even with restricted drivers.
But ATI cards have a new driver released on March 5, 2008, that allows to set this configuration.
I installed them following this guide. Then I went to System/Administration/Graphics and Screen and I selected LCD Panel 1680x1050 (Widescreen).

I hope it helps to you,

---

