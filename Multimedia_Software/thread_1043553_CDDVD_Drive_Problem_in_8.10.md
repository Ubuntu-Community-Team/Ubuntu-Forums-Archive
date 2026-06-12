---
title: "CD/DVD Drive Problem in 8.10"
date: 2009-01-18
forum: Multimedia Software
---

### Post by BoricuaTEK02 on 2009-01-18
I have an Asus G50VM-X1 (laptop) and have it dual booting Ubuntu 8.10 X64 and Vista Home Premium X64. 

Every time I put an Audio CD in, it would read and I would have the ability to play music. Then if I remove the CD and put it back in, it would read and I would hear the CD spin at a high speed. I would then click Places>Computer>CD-RW/DVD+RW Drive and a window comes up saying "Unable to mount location - No media in the drive."

Using the same CD drive to install Ubuntu 8.10, I wouldn't have thought this would be such an issue. 

If anyone knows the steps I can take to correct this problem, I would gladly appreciate it. Thanks!

---

### Post by BoricuaTEK02 on 2009-01-23
I figured it out for future reference people. This would mainly be targeted to those with Asus G50 Models laptops. Other Models...I'm not sure, but give it a go if you like and let everyone else know about your results.

Shutdown computer, go into Bios Setup Utility (Press F2 on the Asus Flaming logo). Go the the "Advanced" tab > SATA > and use "Compatible".

If you want to boot Vista, you will need to put the SATA setting in bios back to "Enhanced".

That's the little work-around I have figured out on my Asus G50VM-X1.

If it still doesn't work, check to see if you've downloaded "regioncode" in the Synaptics Package Manager.

If is still doesn't work, check this last thing out...

[http://lifehacker.com/350015/enable-dvd-playback-in-ubuntu-in-two-commands]("http://lifehacker.com/350015/enable-dvd-playback-in-ubuntu-in-two-commands")

You should be fine by this point.

---

