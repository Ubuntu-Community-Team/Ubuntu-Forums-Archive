---
title: "SB Live"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by mandela on 2007-04-24
I can't hear any sound from my computer. I'm running ubuntu Edgy and my sound card is Creative Labs SB Live! Emu10k1(rev 0a).....then underneath is written:
Subsystem: Creative Labs SBLive!5.1 Digital Mode SB0220.

whatever that means. someone help out pls.
PS: I ran this command modinfo soundcore and this was the result. 

filename:       /lib/modules/2.6.20-15-generic/kernel/sound/soundcore.ko
alias:            char-major-14-*
license:         GPL
author:         Alan Cox
description:  Core sound module
srcversion:   45750F13477CBA5B6F36F46
depends:        
vermagic:       2.6.20-15-generic SMP mod_unload 586

I was finally able to get some sound out but I kinda feel like its not loud enough. Anyone with any advise pls. I'd appreciate.

---

### Post by reclusivemonkey on 2007-04-24
Have you changed any of the levels on the gnome-mixer? Upping your PCM/Wave usually does the trick.

---

### Post by mandela on 2007-04-25
> **reclusivemonkey said:**
> Have you changed any of the levels on the gnome-mixer? Upping your PCM/Wave usually does the trick.
How do I do that?

---

### Post by Steve H on 2007-04-25
If you double-click on the speaker icon on your taskbar, you should be able to access your volume controls. There is also the properties of the Volume Control as well, that allows you to select other volume controls, such as your mic control, etc. So it might be worth having a play around with the different mixer volumes in the ALSA mixer.

Oh! it might be worth checking you are using the ALSA driver for your Soundblaster Live! card. I have the same sound card and mine took a bit of tweaking but it works fine with the ALSA driver (except for the mic doesn't record, but thats another story)

---

### Post by mandela on 2007-04-25
> **Steve H said:**
> If you double-click on the speaker icon on your taskbar, you should be able to access your volume controls. There is also the properties of the Volume Control as well, that allows you to select other volume controls, 

Thanks mate. It worked. I think its much louder now.

---

