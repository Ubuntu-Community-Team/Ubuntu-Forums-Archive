---
title: "No hardware drivers for ATI Radeon X850XT (I want to take advantage of my video card)"
date: 2010-03-05
forum: Multimedia Software
---

### Post by hanzj on 2010-03-05
Hello,
I'm using Ubuntu 9.10. My computer has a video card.
According to ```
lspci | grep VGA
```I have > 
05:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)].

In older versions of Ubuntu, when I go to System/Administration/Hardware Drivers, I would have the option of enabling some driver for my video card. But I see no option today when I went to [Hardware Drivers].

Here is what I want to accomplish: 

[LIST]
[*]I want to use Google Maps with less choppiness and better speed
[*]I want to use Inkscape with my CPU being assisted by the video card.
[*]I want to be able to use Google Earth with less choppiness and better speed.
[*]In other words, I want to harness whatever power my video card can give.
[/LIST]

If i can reach my goals without having to go through [Hardware Drivers], I am open to hearing about it.
Please help.

---

### Post by hanzj on 2010-03-20
Bump.

---

### Post by Melcar on 2010-03-20
Your card is no longer supported by current driver versions.  The last driver release to work with the card is 9.3, which won't work on Ubuntu newer than 9.04.  If you want to use newer versions of Ubuntu you need to rely on the open source driver, which is loaded by default.

---

### Post by hanzj on 2010-03-20
Melcar,
1. Can the open-source driver harness my card's capabilities as well as the close-source driver?
2. How can I confirm that the open-source driver is running?

---

### Post by gordintoronto on 2010-03-20
> **hanzj said:**
> Melcar,
1. Can the open-source driver harness my card's capabilities as well as the close-source driver?
2. How can I confirm that the open-source driver is running?

1. No. But so what.  You still have a usable computer, even though at least one component is ancient. I am in exactly the same position on one of my computers.

2. If you can see this, the open-source driver is running.

---

### Post by hanzj on 2010-03-20
> **gordintoronto said:**
> 1. No. But so what.  


To answer the "So what?" question, without the ATI driver, I can't use graphics-intensive programs (i.e., google earth) without a dramatic slowdown. Google Earth is so slow I don't use it on my computer. That's the "so-what". 8-)

---

### Post by Melcar on 2010-03-21
Check the command _glxinfo_ to see if you got 3d acceleration:

```
glxinfo | grep "renderer string"
```

That should come back with something mentioning DRI and Mesa.  If it says anything about software rendering then the driver is not working properly.  The drivers are only OpenGL1.5 and rather slow, but you should still be able to perform most desktop related 3D tasks and run some games.
You can also try using newer code by getting packages from [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa").  The driver will still have the same basic capabilities, but you may get some fixes and performance boosts.

---

### Post by hanzj on 2010-03-21
melcar,
thanks for the response.
here's the printout of the glxinfo command:> 
OpenGL renderer string: Mesa DRI R300 (R420 5D4D) 20090101 x86/MMX+/3DNow!+/SSE2 TCL

I'll try xorg-edgers next week. 

Thanks!

---

