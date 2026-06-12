---
title: "No GPU hardware acceleration in Chrome/Chromium on Ubuntu 14.10 with Intel graphics."
date: 2014-11-06
forum: Multimedia Software
---

### Post by cdysthe on 2014-11-06
Hi,

After upgrading to Ubuntu 14.10 I no longer have GPU hardware acceleration and WebGL support in Chrome/Chromium. I have of course enabled it chrome://flags like I had on 14.04 but I keep getting "Software only, hardware acceleration unavailable". I'm running a Thinkpad with Intel graphics and have had this working all through 14.04, but not in 14.10. It works in Firefox. What could the problem be?

---

### Post by Rob Sayer on 2014-11-06
Kind of hard to say without knowing exactly which video adapter you're using.

---

### Post by cdysthe on 2014-11-06
It's a Thinkpad T430s with Intel HD4000 graphics (Ivybridge)

It also says under chrome://gpu : 

Problems Detected
GPU process was unable to boot: GPU access is disabled in chrome://settings.
Disabled Features: all

Log Messages
GpuProcessHostUIShim: The GPU process crashed!
GpuProcessHostUIShim: The GPU process crashed!
GpuProcessHostUIShim: The GPU process crashed!

After some digging around I found that if I start Chrome/Chromium with '--disable-gpu-sandbox' acceleration works. I found it referenced here: [https://code.google.com/p/chromium/issues/detail?id=293008](https://code.google.com/p/chromium/issues/detail?id=293008)

---

### Post by cdysthe on 2014-11-24
This is fixed after the latest Intel x server update

---

### Post by jnf-arcor on 2014-11-27
> **cdysthe said:**
> This is fixed after the latest Intel x server update

Hi, for me this is not fixed. My version is xserver-xorg-video-intel (2:2.99.914-1~exp1ubuntu4.1). 
Do you have a newer version, and what is the cause that I don't get it?
Thanks
Jürgen

---

### Post by orengolan on 2014-12-06
> **jnf-arcor said:**
> Hi, for me this is not fixed. My version is xserver-xorg-video-intel (2:2.99.914-1~exp1ubuntu4.1). 
Do you have a newer version, and what is the cause that I don't get it?
Thanks
Jürgen

This solution solved it for me: I launch google-chrome by "LIBGL_DRI3_DISABLE=1 google-chrome".
[https://code.google.com/p/chromium/issues/detail?id=418858](https://code.google.com/p/chromium/issues/detail?id=418858)

---

### Post by cranerja on 2015-01-18
Is there any way to add this to the chrome from the launcher by default?

---

### Post by monkeybrain20122 on 2015-01-18
Indeed.  Just notice this on my 14.10 test partition (which I rarely boot into) In my testing so far (almost 3 months after 14.10 release) I have found no reason whatsoever to trade in 14.04 for 14.10. Basically more buggy, less support for third party software  and much shorter support duration. Many disadvantages and only marginally faster (barely perceptible and can be achieved with some tweaks and upgrading kernel in 14.04)  Also I keep getting notice that Chrome has crashed even though it hasn't.

---

### Post by monkeybrain20122 on 2015-01-18
Ok. I upgraded mesa and the driver with [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers) about:gpu looks good but scrolling and typing (e.g this message)become VERY sluggish. I am now upgrading the kernel and will report back to see if there is any improvement.


Edited: Upgrade kernel to 3.19rc5 , no improvement. Still sluggish tying and choppy scrolling. But webgl works . Firefox doesn't exhibit these problems  though gets much higer fps with the same oibaf driver and kernel 3.19rc5 on Ubuntu 14.04.

---

