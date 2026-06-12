---
title: "Nvidia 319 and 304 packaging or naming problems?"
date: 2013-08-25
forum: Multimedia Software
---

### Post by papibe on 2013-08-25
Hi all

I wonder if any of you are experiencing problems with the latest Nvidia upgrade.

**Context:**
[INDENT]I had 2 12.04 systems. One with a Nvidia 310 card, and another with a 9500. I was running the Steam experimental driver on the 310's and the current on the other.

The 9500's upgrade went flawless, but the one using the experimental ended up on a black screen ([this]("http://ubuntuforums.org/showthread.php?t=2169638&p=12765972#post12765972") is what I did to solve it).
[/INDENT]

**The problem?**
[INDENT]As today (Sun Aug 25 13:33:04 CDT 2013), the recommended driver in additional drivers is 319. However, that is not nvidia-current.

The package that usually is stable, recommended, and is known as nvidia-current, will install 304.
[/INDENT]

Is that a packaging problem?

I appreciate any comments, and any recommendation to address this issue (who's packaging the driver?, how to contact them?, etc).
Kind Regards.

---

### Post by Yellow Pasque on 2013-08-25
Maybe it's related to the 12.04.3 LTS release (and the new lts-raring kernel/X)?

---

### Post by vermontbear on 2013-08-29
My own experience was that the update to 319 was fine until Ubuntu did a kernel update a few days later and then my 12.04 machine went into a cocked hat.  Booted to text login.  Xinit showed that the nVidia drivers were 319, but the kernel was 304.  At that point, I said something like WTF and went back to 304.  I do have a newer EVGA 650 GX card I'd like to try, but I'm not sure I want to waste the time right now, 1) installing 319 from scratch or 2) having to deal with a kernel update that turns back to 304.

Yeah, it probably is related to 12.04.3 and its .... kernel.

Best Regards
John

---

