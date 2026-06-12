---
title: "No HDMI output with open source drivers radeon x1200"
date: 2009-08-12
forum: Multimedia Software
---

### Post by tomsa on 2009-08-12
Hi-

     I am running Jaunty on a Gateway t-1625 laptop with a Radeon x1200 video card.  It has been a huge headache with 9.04.  The latest unsolvable problem for me is that I get no video output when I plug it in to my Plasma TV via HDMI.  I get a picture up until the point that the bootsplash finishes.  When I get to the login screen, I get nothing on the TV, and my laptop screen becomes garbled.  I am using the open source drivers, which work fine, but for this.  Also, if I plug the HDMI cable when I'm already booted up, the display settings find my TV to be a 32" 4:3 screen, rather than a 42" 16:9.  Is there anything that I can do about this?  Can I run the FGLRX from intrepid without borking everything else, or am I just screwed?  Why would it work during bootup and not after?  Google has been no help- any ideas?

---

### Post by tomsa on 2009-08-13
By the way, this is all that I have when I look at my xorg.conf file, and it seems pretty small to me:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by tomsa on 2009-08-16
Here's more info, in case anyone is reading again, or cares to help.  I just discovered the command "xrandr"  and here is it's output:

```
xrandr: Output HDMI-0 is not disconnected but has no modes
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   640x480        59.9     59.4  
HDMI-0 connected (normal left inverted right x axis y axis)

```

Could it have anything to do with the fact that it says the HDMI has no modes?

---

### Post by Major_Rager on 2010-02-12
Same problem here, but I can't get video out via VGA. I think it is because Ubuntu 9.10 does not support Radeon x1200 series. I am about to do a fresh install of 8.10. At least there I could watch my movies on TV, even if it doesn't look as shiny.

---

