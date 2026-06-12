---
title: "ATI Radeon Xpress 200M in Karmic"
date: 2009-11-17
forum: Multimedia Software
---

### Post by mathfreak123 on 2009-11-17
Hey, I did an lshw on my Compaq Presario V5000 to find that it says, "display UNCLAIMED".

I've heard that this means I don't have the driver for my video card installed, so I'm wondering how I can fix that.

Compaq Presario V5000
ATI Radeon Xpress 200M
Mobile AMD Sempron Processor 3300+
768 MB
Ubuntu 9.10

Note that I am a Linux newb, so please be slow in any answers you may have.

---

### Post by Yellow Pasque on 2009-11-18
My display has always said 'unclaimed' as well.

If you want to verify your driver is functioning, look at your /var/log/Xorg.0.log or look at:
```
glxinfo | grep rederer
```
and make sure it returns something like 'Mesa DRI R300...'

---

### Post by mathfreak123 on 2009-11-20
The output of that command returned nothing.

I was able to find these two documents:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

However, they don't offer instructions for 9.10. Should I continue on with them, or should I just wait to see if another solution turns up?

---

### Post by Yellow Pasque on 2009-11-20
Sorry typo:
```
glxinfo | grep renderer
```

---

### Post by mathfreak123 on 2009-11-20
The output is
```

OpenGL renderer string: Mesa DRI R300 (RS400 5955) 20090101 x86/MMX+/3DNow!+/SSE2 NO-TCL
```

Does this mean I have a driver that is working correctly, then?

---

### Post by Melcar on 2009-11-20
yes.

---

### Post by mathfreak123 on 2009-11-20
> **Melcar said:**
> yes.

OK, thank you very much!

---

### Post by Melcar on 2009-11-20
I have a Presario V2000 with that same chip.  Works really well.  I did end up adding some extra power options for the driver.  Could be a placebo effect, but I swear that after those changes battery life went up nearly 10 minutes (which is a lot for my 4 year old lappy).

---

