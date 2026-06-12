---
title: "Major obstacle to Ubuntu widespread adoption: failure to enable VESA mode (installati"
date: 2006-07-21
forum: Multimedia &amp; Video
---

### Post by KillrBuckeye on 2006-07-21
Sorry if this belongs in a different forum, but this topic is fundamentally a video hardware issue.

I was completely new to Linux when I first tried Ubuntu a couple months ago.  I was delighted with how easy it was to install on an older machine--everything worked right out of the box!  However, this delight quickly turned to frustration when I tried to install it on my main machine.  To make a very long story short, my video card (a 7900GT) was very new at the time, and as such there were no drivers bundled with Ubuntu that could support the card.  As a result, when Ubuntu finished installing, the X server failed to start and I was greeted with a series of error messages and an unresponsive black screen with some unintelligible (at least to a Linux n00b) text.  If it hadn't been for my secondary machine and some helpful friends on IRC, I would have completely given up on Linux.  After several hours of searching for solutions and learning many commands, I finally managed to download and install the proprietary nVidia drivers--all in textmode. 

When I described this experience in a couple different posts, I was surprised at how some Linux supporters brushed off the issue and blamed nVidia for not providing open-source drivers.  Well, my response is this:  Why is it that Windows manages to give me a display using VESA drivers regardless of what video card I am using???  IMO, this is a terrible failure of Ubuntu in that it failed to provide me with a GUI when it couldn't recognize my video card.  How will Linux ever become more mainstream if serious issues like this exist?

For a bit more background, this issue occurred with Ubuntu 5.10.  For the knowledgeable Ubuntu users out there, please help me to understand where the breakdown occurred.  The way I see it, the Ubuntu developers simply dropped the ball here.  There's no reason why VESA mode shouldn't have been enabled and GDM started up.  If other OS's can do it, then why not Ubunutu?  Does anyone know if this issue has been corrected in 6.06?

---

### Post by tseliot on 2006-07-21
First of all I agree with you and that's why I suggested this feature for the next release of Ubuntu:
[http://www.ubuntuforums.org/showthread.php?t=201128](http://www.ubuntuforums.org/showthread.php?t=201128)

BTW did you try booting the livecd in "Safe Mode"?

---

### Post by Lord Illidan on 2006-07-21
I totally agree to this.

My Nvidia 6800 card could never work with the nv drivers. Had I not had some modicum of patience and knowledge with the linux OS, I would have quit immediately, when confronted with the meaningless Xserver babble.

Now nv seems to work with my card, but I shudder to think at what could happen if a less competent or patient user tried it before.

Also, how about informing the user on installation, that Linux hardware accellerated drivers are available?

---

### Post by tseliot on 2006-07-21
> **Lord Illidan said:**
> I totally agree to this.

My Nvidia 6800 card could never work with the nv drivers. Had I not had some modicum of patience and knowledge with the linux OS, I would have quit immediately, when confronted with the meaningless Xserver babble.

Now nv seems to work with my card, but I shudder to think at what could happen if a less competent or patient user tried it before.

Also, how about informing the user on installation, that Linux hardware accellerated drivers are available?

I guess that Ubuntu can't include the drivers by default. If you refer only to informing the user then I agree with you.

---

### Post by KillrBuckeye on 2006-07-21
> **tseliot said:**
> First of all I agree with you and that's why I suggested this feature for the next release of Ubuntu:
[http://www.ubuntuforums.org/showthread.php?t=201128](http://www.ubuntuforums.org/showthread.php?t=201128)

Great idea with suggesting that feature.  It's amazing to me that something like that has not yet been implemented.  I mean, it seems like a relatively small undertaking when you consider all that has gone into Ubuntu.

> **tseliot said:**
> BTW did you try booting the livecd in "Safe Mode"?Actually, I could boot in "Expert" mode and manually choose the VESA driver.  This is the only way I could get a GUI with the LiveCD.

---

