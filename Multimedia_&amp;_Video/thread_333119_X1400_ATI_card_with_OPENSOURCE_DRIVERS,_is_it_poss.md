---
title: "X1400 ATI card with OPENSOURCE DRIVERS, is it possible?"
date: 2007-01-06
forum: Multimedia &amp; Video
---

### Post by puccaso on 2007-01-06
i have a spanking new laptop
with a 128M graphics card

but i cant use compiz
cos i have to use the binary drivers

is there anyway i can use the opensource drivers with this device?

when i try tho, all it says is
device not found
like as if the os driver doesnt see the device

help please

---

### Post by cjr2k3 on 2007-01-07
What is the output of:

```
$ fglrxinfo 
```

I have a X1400 with latest binaries and I'm using XGL and Beryl.

---

### Post by puccaso on 2007-01-07
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.6234 (8.32.5)
```

so beryl will work but not compiz?

---

### Post by puccaso on 2007-01-07
oh wait
i dont want to use xgl
it has always caused problems for me
can i not use AIXGL??

---

### Post by CowzRule on 2007-01-07
When you first installed Ubuntu, what driver was installed? If it was the standard "ATI" driver then you "should" be able to use AiGLX. Does Compiz work with AiGLX? I can't say cause I've never tried, but, it does work very well with Beryl.
Unfortunitly for you however is the fact that AiGLX DOES NOT work with the FGLRX drivers. So in order for you to run either Compiz or Beryl you'll have to use XGL or uninstall the FGLRX drivers and use the ATI driver. Or you could wait until ATI/AMD release the next version of the FGLRX driver (They seem to do it every month.) and see if it supports AiGLX.
Good Luck :)

---

### Post by puccaso on 2007-01-07
haha
when i first installed
it used vesa

---

### Post by CowzRule on 2007-01-07
Before installing the 8.32.5 FGLRX drivers, did you try changing your xorg.conf from "VESA" to "ATI"?
If not you could try removing the FGLRX drivers however I tried that once and I couldn't get "direct rendering: Yes" so I reinstalled Ubuntu and setup my xorg.conf to load the "ATI" (also known as "Radeon") driver and AiGLX.
 That's what I'm running now because I have a supported card (x800pro agp). You're card may not be supported because when you installed Ubuntu it installed the "VESA" driver.
I also am having problems getting XGL to work with any version of the FGLRX driver. I posted my problems in this post> [http://www.ubuntuforums.org/showthread.php?t=333542]("http://www.ubuntuforums.org/showthread.php?t=333542")

---

