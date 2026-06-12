---
title: "A question on installing Intel HD GMA drivers"
date: 2014-05-04
forum: Multimedia Software
---

### Post by SoulStreamBurst on 2014-05-04
Hi!

I was wondering on how to install updated drivers for my laptop? Although, I'm not quite sure about the exact model of the graphics card that came built-in on it.

Specs:
Dell Studio 1558 (Intel Core i3 Model) 
Intel GMA HD (The graphics card)
Lubuntu 14.04 (64-bit)

Thanks!

---

### Post by mörgæs on 2014-05-04
Please run ```
lspci -k | grep -A3 VGA
``` and post the results in CODE tags.

---

### Post by SoulStreamBurst on 2014-05-04
Thanks for the response, here's the terminal's output: 

```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
    Subsystem: Dell Device 0413
    Kernel driver in use: i915
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)

```

---

### Post by Yellow Pasque on 2014-05-04
Ubuntu 14.04/Trusty is very recent. Why do you need updated drivers? Are you having issues?

In terms of 3D, mesa 10.1 is the latest release and Ubuntu even pulled some patches from the upcoming mesa 10.2. If you really want to live on the bleeding edge, you can try xorg-edgers PPA.

For X driver, Ubuntu is already shipping very recent development version from git.

For kernel module, there weren't a lot of exciting changes in kernel 3.14: [http://cgit.freedesktop.org/~airlied/linux/commit/?id=859ae233cd0ee76b6143f948ba1cb6b0b4c342f8](http://cgit.freedesktop.org/~airlied/linux/commit/?id=859ae233cd0ee76b6143f948ba1cb6b0b4c342f8)

---

### Post by SoulStreamBurst on 2014-05-04
Oh, is that so? My bad... It  kinda' became a habit of mine installing updated and latest drivers for my system in Windows before. 

So, I guess that isn't the case for Ubuntu/Linux?

---

### Post by Yellow Pasque on 2014-05-04
> **SoulStreamBurst said:**
> So, I guess that isn't the case for Ubuntu/Linux?

For users running the latest release (or the latest kernels in LTS releases), the chance of needing updated drivers is much lower than Windows. There are plenty of exceptions, though, especially with really new hardware.

---

### Post by SoulStreamBurst on 2014-05-05
I see... That explains a lot. 

Well, thank you for taking the time to answer my questions. Boy, I still need to be more familiar with these kind of stuff with Ubuntu/Linux.

Cheers! :D

---

