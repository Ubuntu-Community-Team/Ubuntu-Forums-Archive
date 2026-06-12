---
title: "HANNSPREE HF229H Monitor with ATI X1550 and Ubuntu 8.10 boot problem"
date: 2009-01-16
forum: Multimedia Software
---

### Post by ruakuu on 2009-01-16
Hi, I been trying to install Ubuntu 8.10 on my system, desktop version, it boots ok and the resolution and aspect ration show correctly also the compiz effects.

When running the installer the video shuts down and goes to text mode showing some messages before going to a text mode screen saying something like... "The video servers has been shut down X times in 30 seconds" and that it will wait 2 minutes before trying again, but it just won't come up again so I had to restart and try installing again.

Next I try disabling all the effects, and even the screen saver, and run the installer again, it work this time, but when trying to boot after installation, it goes to the ubuntu loading bar, to end in a black screen, no error message or anything, it just stays there.

I try googling this foe several hours but didn't find anything I could use, so its time to ask hehehe.

Thanks
Rua

---

### Post by ruakuu on 2009-01-18
At first I thought there was a problem with my video card or monitor, but after booting in rescue mode and checking I saw that my /boot was empty, so I try resintalling with the textmode installer, now /boot has the kernel files and GRUB but there's still a problem.

Something weird is going on with my harddrives, I have one IDE and one SATA disk, my SATA is a 300GB disk and I have Windows XP in it, the IDE is a 80GB disk, whats weird is that ubuntu detects them both as SATA disks. 

It detects my IDE disk as /dev/sdb and my SATA as /dev/sda, Im trying to install ubuntu in the IDE disk and boot it with my motherboard boot menu. All the systems files get installed well but at boot time I get an error with hard drive detection and it hangs

I made it work with an older version of ubuntu, the problem was that compiz didn't work, I also try with ubuntu 8.4 but doesn't detect my IDE disk at all.

Both of my disk are set to master, and my sata disk is the one that boots first

This is the model of my IDE drive:
WDC WD800BB-00JHC0

---

### Post by ruakuu on 2009-01-18
Ok, I think I will close this thread and continue in the hardware section. To put it short, there seems to be a conflic with my IDE and SATA drive, after digging more on the internet I found this...

[http://sidux.com/PNphpBB2-viewtopic-t-11103.html](http://sidux.com/PNphpBB2-viewtopic-t-11103.html)

---

