---
title: "[SOLVED] Dual screen setup - DVD / mplayer output problem"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by kko1 on 2007-11-27
Hello.

I have a usable dual screen setup, with a working xorg.conf, with either the "Xinerama" **or** the "Clone" option active. The primary monitor is 1600x1200, the secondary is 1024x768. The problem is not in getting dual screen to work, but in playing DVDs *on the second screen* while using the dual screen setup.

I am using a Matrox G450 card, with no acceleration. (This will be relevant later.) And I'm using Dapper.

```
       Option          "Xinerama" "on"
       Option          "Clone" "off"
#        Option          "Xinerama" "off"
#        Option          "Clone" "on"

```

Now, **the problem** is, when using a dual screen setup, mplayer is acting funny.

*In short, when watching a DVD on the second screen, it doesn't properly stretch the image to 1024*576 pixels, even though (in windowed mode) it shows a full size window. Instead, the real image shown remains the 720x576 pixels, the format it is stored in on the disc.*

***

So, how to solve this:

A) Mplayer can't use the default (XV) video out in Xinerama mode, but crashes. So it has to use the X11 video out, which seems to be part of the cause of the problem. *Does this still happen in newer Ubuntu's (with a newer X), i.e. would an upgrade to (K)ubuntu Gutsy Gibbon help?* **EDIT:** I don't think it would help.

B) For some reason, I haven't been able to use the MGA or XMGA output in mplayer since I moved to Ubuntu. (I seem to not have a */dev/mga*. I suspect that would help. *Any ideas on how to get the (X)MGA drivers working?* **EDIT:** No, this won't help. I found out it only works on the primary head. See [http://ubuntuforums.org/showthread.php?t=632105](http://ubuntuforums.org/showthread.php?t=632105) for details.

C) I have no GL acceleration. (It should only work in 16 bit mode, and I'm using 24 bit depth in my xorg.conf. If I switched it to 16 in dual screen configuration (or even with just a single screen, IIRC), X would hang, and I didn't have the energy to debug at that time. So, I can't use GL output from mplayer, because it's too slow. I don't really want to, either, since I prefer 24 bits. *So forget this.* **EDIT:** Yes, forget this. I get direct rendering (DRI) working, but for one, it's too slow anyway, and for two, it only works for the primary head.

D) Switching to another movie player hasn't worked. I don't have the secondary monitor plugged in constantly, so I haven't experimented too much, but other movie programs I've tried also refused to work in dual screen mode, the time I tried them. *What do you use to watch DVDs in a dual-screen setup?*

E) *I could always switch to a fast enough Nvidia card.* **EDIT:** I won't.

**EDIT:**
F) I've yet to check *if MergedFB would work*. Apparently it could, with 1024*768+1024*768 resolution for the screens, which would just be enough, but I can't be sure.

***

**EDIT:** So, we're left with options D, E, and F. What's your suggested solution? Should I make a poll out of this, option E would probably win, because it's simplest.

**EDIT:** Solved, with - shall we say - option G. See below. ;)

I hope someone has some bright ideas though.

Thank you for any help you may be able to provide.

kko1

---

### Post by kko1 on 2008-02-10
Yay, it works! :KS

This is just too simple. (I mean, why didn't anyone tell me?)

To get a *cloned* second display on Matrox G450, which is enough for me in this particular problem, you don't need anything special. What's more, the output works equally on both heads.

All you need to do is **not use anything *xinerama* or *clone*** at all. In other words, you only configure one screen in your xorg.conf, keep your primary monitor connected to output 1, and connect your secondary monitor to output 2. *The card **automatically** sends the same signal to both.*

So, if you're using a mode that's too big (resolution) or too fast (update frequency) for your second monitor, you get a "signal out of range" on that one. But this is easy. All you need to do is use e.g. *krandrtray* to change to an appropriate resolution and update frequency, and voilà, your both screens have identical outputs.

Bee-au-tiful.

kko1

---

