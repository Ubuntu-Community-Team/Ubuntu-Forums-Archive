---
title: "Xorg locks up overnight using nvidia 7600 gs"
date: 2007-07-15
forum: Multimedia &amp; Video
---

### Post by Barleyman on 2007-07-15
Hi All,

Have been running Ubuntu since Dapper, and recently started having an issue where X would be using 99% of the CPU when left on overnight.    I assume it has something to do with nvidia/twinview drivers for Feisty, but was unable to track down solution.  Since I had upgraded from Dapper->Feisty, I thought I would do a clean install.  

My video card
nvidia 7600 gs

I did 
1. clean install
2. apply all updates
3. install nvidia proprietary driver
4. configure twinview
5. enable desktop effects
6. leave on overnight with top running

To my surprise, still the same problem
Still locked up and top shows Xorg/Compiz eating 99% CPU, even ctl-alt-backspace unresponsive.

I appreciate any help, and have attached my xorg.conf

---

### Post by pppZero on 2007-07-15
I've gone for Compiz/Fusion, so this may not be directly related, but it will at least give you a place to start looking :)

At the very end of the file change ```
Option "Composite" "Disable"
```
to ```
Option "Composite" "Enable"
```

and under Section "Screen" add the following 2 lines:
```

    Option "AllowGLXWithComposite" "True"
    Option "AddARGBGLXVisuals" "True"

```

From what I understand of Xorg (on nvidia hardware at least) is that this actually allows the GFX card to do all of the 3D work, instead of getting the CPU to do it - which would explain all the CPU time being eaten.

The other time I've seen Xorg crash and refuse to let me Ctrl-Alt-Backspace is when the heatsink fell off the chip on my rather old GeForce2. Its probably not that though :)

---

### Post by Barleyman on 2007-07-17
Thanks for the advice, unfortunately that did not fix my problem.  (I restarted X server)

One thing I noticed is even with "Desktop Effects" disabled.  If I grab a window and move it around Xorg eats up to 50% of the CPU.  This just doesn't seem correct.

---

