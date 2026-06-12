---
title: "32bit in windows while 24bit in ubuntu"
date: 2011-10-04
forum: Multimedia Software
---

### Post by yndesai on 2011-10-04
I was always finding that the display color is a bit inferior to 
the MS-windows on the same hardware.

One thing that clearly compare is when i use windows 
the display has the 32bit display option and the colors are much more
sharper. 

While when I am using Ubuntu the best possible support available
is 24bit.

Where should I find the solution.

googling for this have asked me to open /etc/X11/xorg.conf
but now there is no such file in my ubuntu.

Thanks 
YNDESAI

---

### Post by yndesai on 2011-10-04
I have tried 

```
Xorg -pixmap32
```

which seems to have done some improvement. (yet i can not confirm how much is the improvement :()

But the testing site
 
[http://www.labtrain.noaa.gov/config/test_color.htm#Checking%20Color%20Settings](http://www.labtrain.noaa.gov/config/test_color.htm#Checking%20Color%20Settings)

still tells the color depth is 24bit.

---

### Post by wolfen69 on 2011-10-04
If I recall correctly, most people can't tell the difference between 24 and 32 bit colors. Mine is 24bit and looks as good as any computer I've seen. There must be a different reason why colors don't look as good. Are you using any proprietary video drivers?

---

### Post by yndesai on 2011-10-05
There is certainly some difference between the two when you compare the 
MS window.

Since I use the ubuntu from the usb drive I am always checking the display on various computers.

---

### Post by yndesai on 2011-10-07
> **wolfen69 said:**
> If I recall correctly, most people can't tell the difference between 24 and 32 bit colors. Mine is 24bit and looks as good as any computer I've seen. There must be a different reason why colors don't look as good. Are you using any proprietary video drivers?


There is Intel Graphics card and both windows and ubuntu are using Intel driver.

So does it mean that the driver for linux is not as good as the one for windows. :!:

---

