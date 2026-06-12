---
title: "unable to see video after install of 9.04"
date: 2009-07-06
forum: Mythbuntu
---

### Post by Polonius19 on 2009-07-06
The install went find. I picked the default option of backend/frontend. I don't have it connected to my tv yet, i'm using a dell 15fp connected via vga. native resolution on the monitor is 1024x768, but when i boot I can see the splash screen, but shortly there after, the screen goes dark. the light on the front of the monitor goes from green to amber.

my suspicion is that the video is going out of range. in times past, on some linux distros i've had to  use some boot instructions to load some intermediate video mode to configure the card. i haven't found similar instructions for this distro. 

any ideas on a direction i can pursue to find a fix?

---

### Post by philcamlin on 2009-07-06
try booting from live cd does it do the same thing?

---

### Post by Polonius19 on 2009-07-07
i can boot from the live cd. i installed it from the live cd, picking the 2nd option, i was able to go through all the option and config screens. i can boot from the live cd, picking the 1st option, and go through all the screens. i just can't complete the boot from the hard drive. i can see the splash sreen then the screen goes dard and the green light on the monitor turns amber...

---

### Post by Polonius19 on 2009-07-19
nothing?

---

### Post by axelsvag on 2009-07-21
Which hardware do you have?

---

### Post by usmcstitch on 2009-08-06
I have the same issue.  I just spent 2 hours setting up Mythbuntu 9.04 from a live cd.  Configured everything.  On the 1st restart, when it ejects the cd and you go into the OS, i get the splash screen, then some funky color bars at the top, then 2 small Mythbuntu logos, side by side, with the colors all wonky.  It just sits there.  I went into recovery mode, and told it to automatically fix video issues.  Now i don't get anything.  Please Halp!

Hardware:
Core2quad 6600
4GB RAM
ATI 2400XT HD VC
HDHomeRun
Drive SDA - Mythbuntu 9.04
Drive SDB - Win7

The live install went great.  

Thanks for any help you can provide.

---

### Post by gradinaruvasile on 2009-08-06
> **usmcstitch said:**
> I have the same issue.  I just spent 2 hours setting up Mythbuntu 9.04 from a live cd.  Configured everything.  On the 1st restart, when it ejects the cd and you go into the OS, i get the splash screen, then some funky color bars at the top, then 2 small Mythbuntu logos, side by side, with the colors all wonky.  It just sits there.  I went into recovery mode, and told it to automatically fix video issues.  Now i don't get anything.  Please Halp!

Hardware:
Core2quad 6600
4GB RAM
ATI 2400XT HD VC
HDHomeRun
Drive SDA - Mythbuntu 9.04
Drive SDB - Win7

The live install went great.  

Thanks for any help you can provide.

Seems to be a video driver issue. Did u install proprietary drivers?

---

### Post by RowanC on 2009-08-07
I was having similar troubles. I'm not sure if it's because it seems to be setting up only the tvout in the xorg.conf (and if you don't have it plugged in, you won't see anything!)

Try pressing ctrl+alt+F2 (or f2-f6) logging in, and looking 
```
nano /etc/X11/xorg.conf
```

This at least seemed to be my problem - especially, as it seemed to boot up on the monitor, load mythbuntu, but then blackness.

(actually, the first time, it was my fault, as in the mess of cables I'd created setting it all up, I'd forgotten to actually plug the tv into the box!)

---

### Post by SiHa on 2009-08-07
IIRC (it's been a while since I installed) there's an option to enable TV-out, or set the TV standard (PAL / NTSC etc) in the setup screens.
On my machine, if I did that it assumed that I wanted to use the TV, and nothing but the TV, so setup the TV-out as the default output in the xorg.conf

So when the PC boots the video BIOS detects the VGA monitor and squirts everything out there. But when the X server starts up, it looks in xorg.conf, and that tells it to send all output to the TV-out.

Sounds like you have a similar problem.

---

### Post by usmcstitch on 2009-08-07
EDIT:

Frack it.  I just reinstalled!
Used the opensource drivers, then once in the OS, used the restricted.  

Done.

---

