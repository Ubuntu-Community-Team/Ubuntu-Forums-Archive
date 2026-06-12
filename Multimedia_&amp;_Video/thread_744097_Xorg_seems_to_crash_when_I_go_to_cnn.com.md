---
title: "Xorg seems to crash when I go to cnn.com"
date: 2008-04-03
forum: Multimedia &amp; Video
---

### Post by dukemaru on 2008-04-03
My guess is one of the plugins is getting weird on me...
Anyway, the result is that I am brought back to the login screen just as if I ctrl+alt+backspaced.

My best guess is that it might be the flashplayer plugin, but having never experienced this sort of thing before, I'm not confident.

I am running 64bit 7.10
Thanks for any ideas in advance!

---

### Post by SimonHickling on 2008-04-03
If you're using Firefox try adding the FlashBlock plug-in and see if it improves.
That will either confirm or not the flash hypothesis.

BTW when I try cnn.com on 64-bit 7.10 it works OK (with Flashblock)

---

### Post by dukemaru on 2008-04-04
Where did you find Flashblock?
I checked synaptic and found nothing by that name.

---

### Post by ubuntu-freak on 2008-04-04
Sounds like a video driver/xserver problem, I had the same issue in Debian with my Intel chipset. What graphics device do you have? How did you install flash? Is it Adobe?
 
Flashblock is a Firefox extention/add-on by the way, so search for it within Firefox. 


Nathan

---

### Post by dukemaru on 2008-04-04
well, flash may have been the problem. I am using adobe flash 9.
But after installing flashblock, I have no ZERO xorg resets.

I have an nvidia 7800 series card running the new nvidia driver (restricted).
but I have been running this card for 6 months now and never had this kinda problem before with ubuntu.

I'd like to actually make use of flash if possible. Is there an alternative to adobe flash 9 that works well?

---

### Post by ubuntu-freak on 2008-04-04
> **dukemaru said:**
> well, flash may have been the problem. I am using adobe flash 9.
But after installing flashblock, I have no ZERO xorg resets.

I have an nvidia 7800 series card running the new nvidia driver (restricted).
but I have been running this card for 6 months now and never had this kinda problem before with ubuntu.

I'd like to actually make use of flash if possible. Is there an alternative to adobe flash 9 that works well?

 
So flashblock worked? 
 
A manual Adobe Flash install worked well for me, instead of flashplugin-nonfree from the repos. 
 
I recommend you try swfdec once Hardy is released. Works just as well and gives you a "Save as" option in the context menu when you right-click on a Flash vid.
 
Nathan

---

