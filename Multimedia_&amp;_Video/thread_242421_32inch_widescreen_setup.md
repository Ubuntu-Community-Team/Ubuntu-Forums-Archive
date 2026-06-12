---
title: "32inch widescreen setup"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by mikeje99 on 2006-08-23
Hi

I've followed all the guides and the best resolution I can seem to achieve for my 32inch screen is 1024x768 @ 60 mhz.

I really would like to 1360x768 which is the optimum resolution recommened by the manufactur. I've seen it work under Windows Vista so I know it's possible.

The manual says I should be setting 1360x768 @ 60mhz. The H is 47.712khz and the F is 60.015hhz with a Pixel Clock of 85.800mhz

I've posted my xorg.conf as is at the moment. Any help is really appreciated.

Section "Monitor"
	Identifier	"NEC LCD1550V"
       Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"NEC LCD1550V"
	SubSection "Display"
		Depth		16
		Modes           "1024x768_60"
	EndSubSection
EndSection

---

### Post by jeremytaylor on 2006-08-23
Okay. Well get rid of the Modeline in your Monitor settings. You can set Horizontal and Vertical rates by including

        HorizSync       28-80
        VertRefresh     43-60

in the Monitor sectios (put your values in their... I'm just copying and pasting from my xorg.conf.

Next edit your screen section
your mode should read 
Depth   24
Modes  "1360x768" "any other modes you might want"

not sure about the depth, most people run happily at 24bit.

then you're done. Restart your X server and see what happens. 

Jeremy

---

### Post by mikeje99 on 2006-08-24
I did what you said but the screen just flicked on and off. I looked at the screen settings between it flicking on and off and it appeared to be set to 1024x768 by 75mnhz.

I reset the xorg back to the 1024x768 by 60 so I could see what was going on. I then ran sudo 915resolution -l and noticed that the changes I'd made hadn't stayed. I ran 915resolution 3c 1360x768 and then with a -l to see if they'd been set which they had. 

I then restarted X and the screen just went black. I understand now that the reason for 915resolution not staying set is I haven't put it in a startup scipt but I'm reluctant until I can get it to work.

Any Ideas?

Mike]](*,)

---

### Post by mikeje99 on 2006-08-27
Hi

I've checked out my Xorg.0.log file and this is what it says:-

I really would like to get this working if someone willing to help. Please don't let me go back to Bill G.

(II) I810(0): NEC LCD1550V: Using hsync range of 30.00-61.00 kHz
(II) I810(0): NEC LCD1550V: Using vrefresh range of 60.00-75.00 Hz
(II) I810(0): Not using mode "1360x768_60" (no mode of this name)
(II) I810(0): Not using mode "1024x768_60" (no mode of this name)
(--) I810(0): Virtual size is 1368x768 (pitch 1024)
(**) I810(0):  Built-in mode "1360x768"
(**) I810(0):  Built-in mode "1024x768_60.00"
(**) I810(0):  Built-in mode "800x600"
(**) I810(0):  Built-in mode "640x480"
(II) I810(0): Attempting to use 75.00Hz refresh for mode "1360x768" (84d)
(II) I810(0): Attempting to use 60.00Hz refresh for mode "1024x768_60.00" (845)
(II) I810(0): Attempting to use 75.00Hz refresh for mode "800x600" (843)
(II) I810(0): Attempting to use 75.00Hz refresh for mode "640x480" (841)
(II) I810(0): Setting refresh with VBE 3 method.
(II) I810(0): Display plane A is enabled and connected to Pipe A.
(II) I810(0): Enabling plane A.
(II) I810(0): Display plane A is now enabled and connected to Pipe A.
(II) I810(0): PIPEACONF is 0x80000000
(II) I810(0): Mode bandwidth is 47 Mpixel/s
(II) I810(0): maxBandwidth is 1528 Mbyte/s, pipe bandwidths are 126 Mbyte/s, 0 Mbyte/s
(II) I810(0): [drm] dma control initialized, using IRQ 177
(II) Configured Mouse: ps2EnableDataReporting: succeeded

---

### Post by tseliot on 2006-08-27
try with:
```
sudo aptitude install 915resolution
```

and then launch 915resolution

---

### Post by mikeje99 on 2006-08-27
I've tried 915resolution that's when I get the 1360 with the flashing screen.

I've tried changing mode 3c to 1366x768 and 1360x768

Mike

---

### Post by mikeje99 on 2006-08-27
OK I give up. I'm obviously to stupid to run Linux. Fetch me the XP disk. 

Surely it shouldn't be this hard to setup a widescreen.](*,) ](*,) ](*,)

---

### Post by mikeje99 on 2006-08-27
Is it a case of 915resoltion only being able to set 1360x768 @75mhz and not 60mhz?

---

