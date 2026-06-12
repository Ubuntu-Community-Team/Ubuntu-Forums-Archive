---
title: "Problems with 800x600 and 640x480 resolution"
date: 2010-09-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by theosam on 2010-09-06
When I switch to 800x600 and 640x480 screen (or when a applications forces it to those resolutions), it does not force the whole display into my screen. Instead it centers it with two large black bars on both sides (see screenshot).

SCREENSHOT:
[http://img827.imageshack.us/img827/9659/screenshotubuntuforums.png](http://img827.imageshack.us/img827/9659/screenshotubuntuforums.png)

I had no problems with this in Ubuntu 10.04. (I currently have Ubuntu 10.10). 

I have an intel graphics card and driver. My monitor display info says LVDS. I could of sworn it was VGA in Ubuntu 10.04. :???:


Are there any ways to force the display into the whole monitor for 800x600 and 640x480 resolution?

Thanks



*Sorry if I posted in the wrong forum. I don't know if this problem has anything to do with ubuntu 10.10, new kernel, or anything else.*

---

### Post by theosam on 2010-09-06
I ran xrandr

```
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 223mm x 125mm
   1024x600       60.0*+
   800x600        60.3     56.2  
   640x480        59.9  

```

I think I need to connect to VGA1 somehow. 

Any advice?

---

### Post by theosam on 2010-09-06
I think it has something to do with virtual screens.

[img]http://www.osdever.net/FreeVGA/vga/virtual.gif[/img]


Maybe......

Any help is appreciated.

---

### Post by theosam on 2010-09-06
no ideas? :-(

---

### Post by theosam on 2010-09-06
When I switch to 800x600 and 640x480 screen (or when a applications forces it to those resolutions), it does not fill the screen. See screenshot.


SCREENSHOT:
[http://img827.imageshack.us/img827/9659/screenshotubuntuforums.png](http://img827.imageshack.us/img827/9659/screenshotubuntuforums.png)

I had no problems with this in Ubuntu 10.04. (I currently have Ubuntu 10.10). 

I have an intel graphics card and driver. My monitor display info says LVDS. I could of sworn it was VGA in Ubuntu 10.04. 


Are there any ways to force the display into the whole monitor for 800x600 and 640x480 resolution?

Thanks

---

### Post by TNT1 on 2010-09-06
a) your pic appears to be blank, and b) have you enabled display expansion in BIOS?

---

### Post by theosam on 2010-09-06
I fixed the picture

[http://img827.imageshack.us/img827/9659/screenshotubuntuforums.png](http://img827.imageshack.us/img827/9659/screenshotubuntuforums.png)


How do I do enable display expansion?

---

### Post by TNT1 on 2010-09-06
> **theosam said:**
> I fixed the picture

[http://img827.imageshack.us/img827/9659/screenshotubuntuforums.png](http://img827.imageshack.us/img827/9659/screenshotubuntuforums.png)


How do I do enable display expansion?

Better.

Generally, I have only seen monitors like your pic when display expansion is disabled.

When you boot, go into your bios setup and look for an option relating to your display.

---

### Post by theosam on 2010-09-06
There are no display settings under BIOS. And resolution works on my Windows partition.

---

### Post by overdrank on 2010-09-06
Hi, please do not create multiple threads on the same issue. Threads merged and moved to Maverick Meerkat Testing and Discussion. :)

---

### Post by theosam on 2010-09-07
"This is because Ubuntu 10.10 has an unsupported version of Xorg. You need to revert to the lucid version to alleviate the problem."

[http://ubuntuforums.org/showpost.php?p=9806221&postcount=7](http://ubuntuforums.org/showpost.php?p=9806221&postcount=7)

That solved the problem. (Note: I am running in a seperate partition not in a virtual box).

---

### Post by cariboo on 2010-09-07
The Intel i915 driver is fully support in Maverick with Xorg 1.9

---

### Post by theosam on 2010-09-07
I tried the 2.6.32 kernel while keeping Ubuntu 10.10 . Strangely enough, this fixes the problem completely.

Sorry for the misunderstanding, cariboo907.

---

### Post by Trespasser on 2010-09-11
Just wanted to add that I have the same problem with my Lenovo G530 with an Intel mobile 4 graphics card and kernel 2.6.35...black bars on both sides of the display screen at resolution 800x600, so you're not alone on this one theosam.

Later...

---

### Post by cariboo on 2010-09-11
can you change the monitor frequency setting?

---

### Post by theosam on 2010-09-11
I can do 56 Hz refresh rate under 800x600. The other resolutions are fixed on 60 Hz. Changing it to 56 Hz under 800x600 does nothing.

---

