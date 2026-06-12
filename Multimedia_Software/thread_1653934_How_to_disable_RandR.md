---
title: "How to disable RandR?"
date: 2010-12-27
forum: Multimedia Software
---

### Post by Gforce20 on 2010-12-27
I'm attempting to disable RandR so that fglrx can control X without interference. I've already followed [this advice](http://ubuntuforums.org/showpost.php?p=7170485&postcount=2) from another thread, but aticonfig still indicates that RandR is active:

```
$ aticonfig --enable-monitor=0
Error: option --enable-monitor is not supported when RandR 1.2 is enabled!
```

Xorg.0.log does not seem to clearly indicate either way.

```
$ cat Xorg.0.log | grep -i randr
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(WW) fglrx(0): Option "EnableRandR12" is not used
(II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
(--) RandR disabled
(WW) fglrx(1): Option "EnableRandR12" is not used
(II) fglrx(1): Disabling in-server RandR and enabling in-driver RandR 1.2.
(--) RandR disabled
(II) Initializing built-in extension RANDR
(II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
(II) fglrx(1): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
```

For what it's worth, here's the output of xrandr as well. Note that I have two screens, one 1440x900 and the other 1280x1024:

```
$ xrandr
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1440 x 1440
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9*+
   1280x1024      75.0     60.0  
   1280x960       75.0     60.0  
   1280x800       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       74.9     59.9  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     70.0     60.3     56.2  
   720x480        60.0  
   640x480        75.0     72.8     60.0  
CRT2 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)
CV disconnected (normal left inverted right x axis y axis)
```

I've read that it's possible to recompile X without RandR, but I'd rather not take such drastic measures until I've exhausted all other possibilities. What else do I need to do to disable it?

---

### Post by Gforce20 on 2010-12-27
I think I now understand exactly what is going wrong. The advice in the aforementioned thread said to do two things in order to disable RandR - the first involved xorg.conf, and the second involved fglrx. One of these must be failing:

```
(WW) fglrx(0): Option "EnableRandR12" is not used
(II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
```

[s]Because these lines appear twice in my Xorg.0.log output, I am led to believe that[/s] the culprit is my xorg.conf[s], which specifies EnableRandR12 twice:[/s]

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[0]-1" LeftOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option      "EnableRandR12" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
	Option      "EnableRandR12" "false"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1440x900" "1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

[s]I'll try commenting out one of the lines to confirm this.[/s] Yep, xorg.conf doesn't recognize EnableRandR12 as a real option. Any ideas?

---

### Post by tjones00 on 2010-12-27
Maybe the last post on this thread will work.

[http://forums.amd.com/forum/messageview.cfm?catid=310&threadid=110989](http://forums.amd.com/forum/messageview.cfm?catid=310&threadid=110989)

The guys over at phoronix are trying to sort this out as well.

[http://www.phoronix.com/forums/showthread.php?p=163377](http://www.phoronix.com/forums/showthread.php?p=163377)

---

### Post by Gforce20 on 2010-12-27
> **tjones00 said:**
> Maybe the last post on this thread will work.

[http://forums.amd.com/forum/messageview.cfm?catid=310&threadid=110989](http://forums.amd.com/forum/messageview.cfm?catid=310&threadid=110989)

This was in the thread I mentioned in my first post.

> **tjones00 said:**
> The guys over at phoronix are trying to sort this out as well.

[http://www.phoronix.com/forums/showthread.php?p=163377](http://www.phoronix.com/forums/showthread.php?p=163377)
Good to hear I'm not the only one having issues with it.

---

### Post by jlewis05 on 2011-04-24
I have been experiencing the same issue, is there any update or new information out there that might solve this?  I stopped X and changed the pcs-str to no avail.

Thanks,
John

---

