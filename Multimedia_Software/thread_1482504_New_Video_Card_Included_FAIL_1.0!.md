---
title: "New Video Card Included FAIL 1.0!"
date: 2010-05-13
forum: Multimedia Software
---

### Post by naltoidaddict on 2010-05-13
I have a Dell Inspiron 530s (the low profile one) running Ubuntu 9.  It ran fine with the onboard video card but I wanted dual monitors so I put an ATI dual head card into it.  That kinda' worked but all the video "enhancements" stuff broke.  I read online that Linux doesn't like ATI too much so I bought a PCI dual dvi Nvidia GeForce 8400.  It posts fine and I get the initial ubuntu splash screen, but looks like when it goes to start x it flips out, almost like the refresh rate is too high.  Basically, I have to hold the power button to get it to shut down.  Is there anything I have to "prep" before I switch to this card?  Or does it sound like there's just an incompatibility?

---

### Post by vandorjw on 2010-05-13
Are you still running Ubuntu 9.10? or did you move to 10.04?

I know that Xorg no longer requires a configuration file. If you have one, please remove it.
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

```

Then restart the computer, and try again.

Another thing, when you put in the ATI cards, did you install any drivers for them? The catalyst suit? If you did, please remove that also.

Another thing to look for, does the Geforce 8400 work in windows?
Older Geforce 8*** series have problems.
-----------------------------------------------------------------
A simple way to test if it is a configuration problem and not a Hardware problem.
1. Take a live CD and use it to boot up your computer. (preferably 10.04, but doesn't matter if it is not)
2. If it checks out, its a configuration problem in your installed system.
3. I would then mount your hard drive, and proceed to mv the xorg.conf file. (or just straight up delete it)

---

### Post by naltoidaddict on 2010-05-14
Booted up on my install disk and it did the same thing.  No worries, I pulled the video card and went back to the onboard card.  I can wait until a hardware refresh for dual monitor.  Before I buy I'll make sure it has a compatible video card.

  Thanks for your help cc7gir.

---

