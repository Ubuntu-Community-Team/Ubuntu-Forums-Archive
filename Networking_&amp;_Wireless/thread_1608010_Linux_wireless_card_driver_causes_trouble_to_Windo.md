---
title: "Linux wireless card driver causes trouble to Windows"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by youbaji on 2010-10-28
Hello all,
I have Atheros 5212 chip on my Thinkpad T61.  After upgrading to ubuntu 10.10, I was not able to use wireless network.  The hardware was detected but couldn't find any access point.  Then, one day I boot up Linux with hibernated Windows, my wireless network in Linux came alive.  However, when I boot back to Windows, Windows was not able to start wireless card anymore.  I tried update drivers in Windows, no luck.  I also changed drivers in Linux from ath5k to ath_pci(I built it from madwifi), still not work.  I wonder if Linux driver has set my card into a state that confused Windows.
Is there a way to hard reset the card?  How can I have it work both in Windows and Linux?

Thanks!

---

### Post by grahammechanical on 2010-10-28
I am not an expert. I really do not know what I am talking about. I saw your post 3 hours ago before I went to have my tea. I now see that no one has helped you. Can I share my thoughts with you?

Do you have a user guide that came with the laptop? Does it recommend hibernating with the wireless card switched on or switched off? It is my guess that if wireless was on when you put Windows into hibernation, then Windows would expect wireless to still be on when it resumes from hibernation.

When you shutdown from Ubuntu it is possible (I do not really know) that Ubuntu switched off wireless as it shut down. May be Windows is indeed confused. I could be wrong of course.

Is there a way of switching the wireless card in the laptop on and off by pressing a key on the keyboard? May be you need to do that and then reboot into windows. May be you have already tried all of this.

I suspect (I have no proof) that carrying out a shutdown, suspend or hibernation with wireless still switched on will cause problems at the next reboot or resume. I think that this might happen with Windows and Ubuntu.

This is all I can think of to help you.  Regards.

---

### Post by youbaji on 2010-10-31
Thank you for your suggestions!  I have tried different combination like turn on/off wireless before/after boot up; switch Linux Drivers; none of them worked.
I gave up and got a new wireless card :(, it worked fine with Windows.  To prevent Linux mess up this card again.  I moved Linux wireless drivers folder to another place.

---

