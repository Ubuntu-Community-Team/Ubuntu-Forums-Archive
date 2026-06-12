---
title: "Don't get it... i810 and 60Hz"
date: 2006-06-12
forum: Multimedia &amp; Video
---

### Post by yopnono on 2006-06-12
I have a flatscreen philips 170B that they recommend to use 60Hz. But I really can't get xorg to obey my settings, it's only like to use 75Hz.
Video driver id i810. If usig VESA it work fine except the there is no acceleration.

Well I can force it by using.
```
# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -HSync +Vsync
```

Then I get it to use 60Hz but ..... then the GDM is messed up, I need to mouse scroll to view the whole GDM screen.

---

### Post by yopnono on 2006-06-16
Ok I have solved it.
If using the i810 driver on my philips 17" that support up to 75hz but recommended 60hz, I just cant set the i810 to use 60hz...

If I use modeline like:
```
# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -HSync +Vsync
```
Then it uses 60hz like I want it. but.... the GDM is using virtual 1600x1200 = really big on a screen that only support 1280x1024.

So I had to install 915resolution and set it to use 1600x1200 as 1280x1024.
And also use the Modeline in my xorg file.
```
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=3a
#
# and set resolutions for the mode.
#
XRESO=1280
YRESO=1024
#
# We can also set the pixel mode.
# Please note that this is optional,
# you can also leave this value blank.
BIT=8
```
Now I have the GDM in 1280x1024@60hz, also the desktop in 1280x1024@60hz. 

Really don't see why i810 don't just let me select the hz I wan't, since it's detecting my sceen as a philips 170 TFT that should use 60Hz.

---

