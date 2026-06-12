---
title: "Audio problems and more. I am at a loss."
date: 2007-03-14
forum: Multimedia &amp; Video
---

### Post by antonio97b on 2007-03-14
Ok.

I am very frustrated at this point. I can not get any audio out of my logitech 350 headset (my only source for sound). I have been searching the forums and the web for help for about 6 hours. I follow this guide and that guide and it is starting to do more harm then good. I'm now locked out of adept becuase something else is using the packaging database. Restart doesn't help, and even when it was working I couldn't install anything audio related because it interfered with other things audio related (I forget now.). Amarok won't start now because some other guide told me to tweak it and now its broken also.

I don't understand why all of the guides I have been following for the past 6 hours have only hurt my situation more. Not one thing (not one) has helped. Do I just throw in the towel and reinstall or is there something someone can do for me? I do know that my my headset is recognised, just nothing comes out of it.

I am on Kubuntu 64bit and I have onboard audio on my motherboard (asus A8V-E SE).

---

### Post by ssavelan on 2007-03-14
> **antonio97b said:**
> Ok.

 I follow this guide and that guide and it is starting to do more harm then good.

 Do I just throw in the towel and reinstall.

I am on Kubuntu 64bit and I have onboard audio on my motherboard (asus A8V-E SE).

Well, yes, I have and would.  I tangled many an ALSA configuration and totally destroyed any semblance of hope on a number of installs.

The good news: you can find a stable path to sound heaven.

I would recommend i386/x86/generic over 64-bit for now.  As far as I am aware, the 64-bit image is still fraught with media issues.  I have been running x86 on an AMD Opteron and it seems to make good use of both procs.  The only advantage to 64-bit, in my situation, is that the SAGE mathematical software claims that it is slightly better supported for ubuntu-AMD64.  I however have run into no problems with the 32-bit.

That having been said...

The latest version of ALSA seems to be superior to the ubuntu defaults with a number of interfaces.  I am not familiar with the logitech; however, I have never had problems with 32-bit ubuntu and any onboard sound interface.  Did you ever have sound?  The headphones are standard mini(as opposed to usb)?


THAT HAVING BEEN SAID:

I personally recommend setting up two partitions so you can wreck configurations with abandon.  You may not have time for such non-sense.  But, I found that multiple partitions helped in my experimental (what's ALSA?) phase.  I can now usually (always?) set-up a friend with any supported interface (supported by ALSA) pretty quickly and get all of their favorite media going.

I have never completely set-up the 64-bit to play all formats.

Unless you are really attached to KDE, I like GNOME and xfce.  Xubuntu actually might be my favorite especially under a gig of memory/pre-Opteron.  I suppose that is just preference, but the standard ubuntu often surprises me with its convenient defaults.

---

