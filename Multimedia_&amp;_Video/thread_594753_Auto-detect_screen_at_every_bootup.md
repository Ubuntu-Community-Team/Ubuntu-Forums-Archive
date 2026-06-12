---
title: "Auto-detect screen at *every* bootup?"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by Zugzwang on 2007-10-28
Hi all,

Although playing around with Linux distributions for ~ 2 years now on my personal laptop, I'm afraid that I am still Windows user since there is one critical issue that no Linux distribution ever managed to handle:

As far as I know, the "light bulb" of the laptop screen is subject to wear-out, so I'm using an external screen whenever at home or somewhere else there is one. When using Windows, it suffices to plug it in before booting the computer to make sure that the internal screen of the laptop is never switched on. The internal screen resolution is 1280x800, but I'm using an ordinary 4:3 CRT external screen. When using Windows, I'm getting a clear picture with various different screens, even with those that do not support DPMS. The screen resolution is set automatically. If no external screen is plugged in, the resolution is automatically set to 1280x800.

This doesn't work at all in gutsy (using the new Screen/resolution manager):
-  First of all, there is no 1280x800 resultion to choose (even if I manually choose a 1280x800 LCD as my monitor).
- When using an external screen, it is heavily misconfigured (Barrel distortion, etc.).

I wouldn't mind having to switch the resolution once booted but at the moment, Linux is -again- unusable for me. Edgy used to switch on and off the internal monitor two times before using the external one which is also likely to cause additional wearout. At least this issue is fixed.

There would be two possible solutions:
- At bootup, one of the configurations for the screen manager is automatically chosen using the identification of the screen attached.
- *Working* autodetection is applied at every bootup.

It would also be nice to be able to switch on dual-screen mode *after* bootup.

I'm using the nv driver on a GeForce GO 5200 - It's a Toshiba Satellite Pro A30, Pentium-M 1.5Ghz, 512MB Ram, Ubuntu Gutsy. I haven't tried the nvidia-drivers since as far as I know, there is no sufficient RANDR support by now. Right?

Thanks!

---

### Post by Zugzwang on 2007-10-30
I just wanted to mention that this problem is still relevant, so don't hesitate to answer if you think that you know a solution. :-\"

---

### Post by Mcavity on 2007-10-30
I have a similar problem with guts freaking out about my displays. though I did find the cd for my lcd that had the inf file on it and that hepled a bit after I imported it. 
[not 100 percent I still get some weirdness]

---

### Post by Zugzwang on 2007-10-31
> **Mcavity said:**
> I have a similar problem with guts freaking out about my displays. though I did find the cd for my lcd that had the inf file on it and that hepled a bit after I imported it. 
[not 100 percent I still get some weirdness]

I'm afraid that it appears as if most laptops do not ship with a CD containing such a file. It looks like as it's even quite a tough task to find out what's the name of the screen built in.

---

### Post by Zugzwang on 2007-11-04
I really wonder that the X-Server doesn't automatically distinguish between the internal and external screen as this is a standard feature in many Windows display drivers... or does it?

---

