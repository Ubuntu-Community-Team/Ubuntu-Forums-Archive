---
title: "Nvidia Geforce6150se - slow 3d graphics, compiz, firefox, ect"
date: 2009-12-03
forum: Multimedia Software
---

### Post by Don Scapp on 2009-12-03
Hi there,

I have an Nvidia Gefore6150SE, I'm using the latest propietry drivers and am getting terribly slow graphics with it under compiz (wobbly windows, desktop spinning, ect is slow framrate), scrolling in firefox is slow, and even SuperTux2 runs sluggish! The only distro I've had sucess with after install is MandrivaOne, but I want the same speed of graphics in Ubuntu! Does anyone have any idea what could be the problem?

Thanks,
Don.

---

### Post by lidex on 2009-12-03
Which version an architecture of ubuntu are you using? Was this an initial issue or new? 
This is an older chip - did you check for compatibility with driver? What driver are you using?

---

### Post by Don Scapp on 2009-12-04
9.10, as far as I know it's always been like this, yes, it works really well as I said in my installation of MandrivaOne, but I love Ubuntu and wish I could have the same fps/smooth correctly working graphics, the very latest version as installed via the hardware drivers dialog.

Should I prehaps compile the nvidia driver on my system and install it, or would that make no difference?

Don.

---

### Post by Don Scapp on 2009-12-08
Sorry to bump, but I really don't know how to improve the fps in ubuntu and can't do any sort of game playing with it. If anyone has any ideas on what I could try, I'd be very grateful!

---

### Post by lidex on 2009-12-08
See this thread:
[http://ubuntuforums.org/showthread.php?t=1159449]("http://ubuntuforums.org/showthread.php?t=1159449")
Try the 173 driver and see what happens.

---

### Post by Don Scapp on 2009-12-09
Hi there,

I can confirm that neither the 173 driver nor the 90 driver work any better; I believe I tried this before and JUST attempted it on a fresh install.

Is there a differnt way of installing the drivers on ubuntu outside of the Hardware Drivers tool?

---

### Post by Don Scapp on 2009-12-10
Has anyone managed to get this card working properly in ubuntu, and does anyone know why Mandriva might be fine with it, but no other distro can run at the correct fps?

---

### Post by Don Scapp on 2009-12-30
I found, the whole thing is caused by the default drivers Display settings being 65hz, and is simply fixed by adjusting the settings under Compiz refresh rate/detect refresh rate section!
 
 Thanks to all who helped!

(I've also used posted this solution on my other older threads in case anyone stumbles across them in the future.)

---

