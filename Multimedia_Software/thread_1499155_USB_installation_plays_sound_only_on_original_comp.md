---
title: "USB installation plays sound only on original computer"
date: 2010-06-01
forum: Multimedia Software
---

### Post by MyiEye on 2010-06-01
So, I installed Ubuntu to a flash drive and it worked all dandy like. However, on other computers the audio doesn't work, neither can I install a driver for the graphics card to use effects and (at least so it seems to me) run 3D games. Is it trying to use the same hardware that it did on the first computer I used and therefore hasn't installed the right stuff?

Thanks a lot!

EDIT: I can 'play' music, so I think the codecs are fine, but no audio comes out, so I'm thinking it must be a driver problem.

EDIT2: Apologies, I checked the "Comprehensive sound problems solution guide" and was able to fix the audio simply by unmuting the speakers. However, the graphics problem remains.

One other tid bit that might be relevant is that the first time I booted up on a different computer it did tell me (in different wording) that the graphics might have trouble because it was set up for a different hardware system, so I told it to set up a new configuration and that seemed all dandy.

Thanks again.

---

### Post by C.S.Cameron on 2010-06-01
There used to be an application in the repositories named switchconf that would allow you to select different xorg.conf files on boot.
It was great for selecting nvidia drivers, dual monitors etc when using various computers.
I don't think it works on modern versions of Ubuntu though.

---

