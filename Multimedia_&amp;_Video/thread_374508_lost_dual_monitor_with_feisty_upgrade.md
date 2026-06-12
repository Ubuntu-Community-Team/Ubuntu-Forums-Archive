---
title: "lost dual monitor with feisty upgrade"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by aambrose on 2007-03-02
I've been using ubuntu on my T42 laptop since Breezy, and had the dual monitor
setup thru the Thinkpad dock.  I had 1600x1200 on the external monitor, and a
1400x1050 window into the larger desktop on the laptop.  I was a happy camper.
I upgraded to Feisty a couple weeks back, and I was still in
dual-monitor-nirvana.

This past Tuesday (Feb 27), there was a large set of updates for Feisty, which
I believe contained xorg updates.   At that point, Happy Dual-Monitor Days were
over.  :(   Now, both monitors show up in 1400x1050 @ 60Hz (making for a blindness-inducing external monitor experience).

The following seem to be the relevant parts from Xorg.0.log:


(II) RADEON(0): Primary:
 Monitor   -- LVDS
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- NONE
 DDC Type  -- NONE
(II) RADEON(0): Secondary:
 Monitor   -- CRT
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): PLL parameters: rf=2700 rd=6 min=20000 max=35000; xclk=21000
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): Panel ID string: SXGA+ Single (85MHz)    
(II) RADEON(0): Panel Size from BIOS: 1400x1050
(II) RADEON(0): BIOS provided dividers will be used.
(II) RADEON(0): Total number of valid DDC mode(s) found: 0
(II) RADEON(0): Valid mode using on-chip RMX: 1400x1050
(WW) RADEON(0): Mode 1600x1200 is out of range.
(WW) RADEON(0): Valid modes must be between 320x200-1400x1050


Any ideas why the valid modes police are now cracking down on my poor external
monitor?  


The following is my xorg.conf device and monitor sections:


Section "Device"
    Identifier	"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
    Driver		"radeon"
    BusID		"PCI:1:0:0"
    Option		"MonitorLayout"	"LVDS,CRT"
    Option		"MetaModes"	"1400x1050-1600x1200"
    # acceleration
    Option          "AGPMode" "4"
    Option          "EnablePageFlip" "on"
    Option          "RenderAccel" "on"
    # use bios hot keys on thinkpad (aka fn+f7)
    Option          "BIOSHotkeys" "on"
EndSection


Section "Monitor"
	Identifier	"Sony G500"
	Option		"DPMS"
	HorizSync	30-121
	VertRefresh	48-160
EndSection



Thanks!

---

### Post by surfingpenguin on 2007-03-15
I have the same problem.

---

