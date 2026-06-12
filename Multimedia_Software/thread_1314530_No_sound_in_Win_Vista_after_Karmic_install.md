---
title: "No sound in Win Vista after Karmic install"
date: 2009-11-04
forum: Multimedia Software
---

### Post by whirlwind on 2009-11-04
Running a fully updated version of Karmic i386, my sound card is an SB Audigy.  It shows in Ubuntu as CA106.

I haven't heard sound from my Audigy in Windows Vista 64 since the installation of Karmic, except for one time when I got a BSOD in windows and rebooted into windows the sound worked fine. I have not for the life of me been able to get working sound in Windows with various reset/cold reboot combinations.

Any ideas?  Karmic is fantastic BTW, best Linux installation I've had.

Thanks

Posted here after wrongly being posted in Multimedia Production, sorry.

---

### Post by wilee-nilee on 2009-11-04
So if you are dual booting then te Karmic install should not effect sound in Vista. Is it a Wubi or dual boot. Even Wubi probably shouldn't have caused the lack of sound situation. This sounds more like a hardware issue. It will be almost impossible to diagnose the problem without more information like the install and if you have sound in Linux.

---

### Post by whirlwind on 2009-11-04
> **wilee-nilee said:**
> So if you are dual booting then te Karmic install should not effect sound in Vista. Is it a Wubi or dual boot. Even Wubi probably shouldn't have caused the lack of sound situation. This sounds more like a hardware issue.
I am dual booting, and I agree that I can't see a reason why an Ubuntu install would cause me to lose sound in Windows.  I was dual booting Fedora 11 previously with no issues, but once I installed Karmic over my Fedora partition I no longer had sound in Windows.  I have absolutely no issues with sound in Karmic on the same device.

The hardware worked perfect before, and continues to do so in Karmic.  

whirlwind

---

### Post by wilee-nilee on 2009-11-04
> **whirlwind said:**
> I am dual booting, and I agree that I can't see a reason why an Ubuntu install would cause me to lose sound in Windows.  I was dual booting Fedora 11 previously with no issues, but once I installed Karmic over my Fedora partition I no longer had sound in Windows.  I have absolutely no issues with sound in Karmic on the same device.

The hardware worked perfect before, and continues to do so in Karmic.  

whirlwind

Well your on the right track with more info, so it sounds like a driver issue in vista or maybe even something even simpler, hopefully somebody will have a way of getting to the bottom of this. I suggest driver not really knowing what I'm saying but, just as a point of conjecture.

---

### Post by cscj01 on 2009-12-02
I have the same problem with a dual boot of Karmic and XP, 32 bit.  This actually worked fine for several weeks after the upgrade.  Then, no sound in XP.  If I do a shutdown and boot, XP has sound.  If I just do a restart, no sound in XP.  My guess is pulse audio is "configuring" the SB Audigy in a manner so that XP cannot use it.

If I look at Device Manager in XP, the card status is ok.  If I try to do diagnostics, nothing helps.  I have not spent much time on this as I only use XP occasionally these days.  But for a couple of items, I would not use XP at all.

---

### Post by Mnew2Linux on 2010-04-05
I am dual booting as well and recently upgraded to Karmic.  I'm having the same issue with no sound and a SoundBlaster Audigy.  Any fixes for this?

> **cscj01 said:**
> I have the same problem with a dual boot of Karmic and XP, 32 bit.  This actually worked fine for several weeks after the upgrade.  Then, no sound in XP.  If I do a shutdown and boot, XP has sound.  If I just do a restart, no sound in XP.  My guess is pulse audio is "configuring" the SB Audigy in a manner so that XP cannot use it.

If I look at Device Manager in XP, the card status is ok.  If I try to do diagnostics, nothing helps.  I have not spent much time on this as I only use XP occasionally these days.  But for a couple of items, I would not use XP at all.

---

### Post by cscj01 on 2010-06-03
I have upgraded to Lucid, and sound works correctly in both XP and Lucid after reboots.  So whatever the problem was has been fixed.

---

