---
title: "Maximizing windows with video freezes ubuntu"
date: 2009-05-05
forum: Multimedia Software
---

### Post by jeppo on 2009-05-05
Hi there,

As the title says, when I maximize a window with a video playing in it, for example totem or VLC, the system hangs.  The screen goes blank and the computer is unresponsive, requiring a hard reboot.

This doesn't happen every time, but it happens more often than not.  Very frustrating as I watch a fair few videos on my computer.  I'm running an ATI Radeon HD 3430 video card with restricted drivers.

Any help would be great,
jeppo

---

### Post by Alajjana on 2009-05-16
Try to disable Compiz.

---

### Post by jeppo on 2009-05-16
Thanks for the reply Alajjana,
Disabling compiz solves the problem, however I would really like to have the effects and be able to resize videos at the same time.

Not sure if it's relevant, but AWN shows up a warning saying:
Warning: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

Thanks for your help,
Chris

---

### Post by VastOne on 2009-05-16
> **jeppo said:**
> Thanks for the reply Alajjana,
Disabling compiz solves the problem, however I would really like to have the effects and be able to resize videos at the same time.

Not sure if it's relevant, but AWN shows up a warning saying:
Warning: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

Thanks for your help,
Chris

When you disable compiz, you disable AWN's brain to run....

Is your Radeon an onboard chip or an installed card?  

I went away from nVidia on a new build and tried the Radeon HD3320...(or something similar)...Ended up disabling it and getting a 55 dollar 1 gig GeForce 9500 GT because of what yours is doing..It drove me nuts...And it was any video in full screen...I thought it was because of the new 9.4 ATI drivers, but it appears that it is deeper than that...

---

### Post by jeppo on 2009-05-16
Oh yeah I understand that AWN uses compiz, what I didnt say is it appears that the error is in the background when compiz IS enabled, but you only see it for a second when the computer is shutting down.

Anyway, yeah it's onboard in my laptop.  It's frustrating as it doesn't just crash the program but the entire OS.

---

### Post by VastOne on 2009-05-16
> **jeppo said:**
> Oh yeah I understand that AWN uses compiz, what I didnt say is it appears that the error is in the background when compiz IS enabled, but you only see it for a second when the computer is shutting down.

Anyway, yeah it's onboard in my laptop.  It's frustrating as it doesn't just crash the program but the entire OS.

There is a new ATI 9.5 out that says it addresses and fixes the full screen issues, you may want to give it a try.

---

### Post by cooco on 2009-05-17
It happens to my thinkpad t61 with nvidia video as well but it happend to me also when I tried to maximize firefox once.

---

### Post by jeppo on 2009-05-17
How do I install 9.5?

---

### Post by xc3RnbFO8P on 2009-05-17
If you are using Compiz, try in settings/preferences/compiz config settings manager under general tab uncheck Unredirect fullscreen.

---

### Post by RichardCain on 2009-05-17
I've got the same problem, but using 8.04 Hardy.  It only started recently, but it happens every time, not just sometimes.  Sometimes it goes black, sometimes it's bright blue - very similar the the <i>screen of death</i>.
Totem and Mplayer both do it.  VLC used to do it until I uninstalled it.  I wanted to uninstall all players and start again, but it won't let me; it says other applications depend on them.

---

### Post by jeppo on 2009-05-17
> **Ringi said:**
> If you are using Compiz, try in settings/preferences/compiz config settings manager under general tab uncheck Unredirect fullscreen.
Thanks for the suggestion, but I tried that and the same problem happened.  So basically what it's narrowed down to is Compiz or ATI drivers or a combination of the two.  Does this sound right to you Richard?  ie, do you have an ATI card and/or Compiz installed.

---

### Post by montini on 2009-05-18
exact same with Jaunty nvidia restricted driver (180 i guess) and compiz. Freezes on window maximization. So it's not only ATI.

EDIT: mine is freezing on skype window or .pdf document view maximization, not just any window. Videos (totem or VLC) are played ok in fullscreen.

---

