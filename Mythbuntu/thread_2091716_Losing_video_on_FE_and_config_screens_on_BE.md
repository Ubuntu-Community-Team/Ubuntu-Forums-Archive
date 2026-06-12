---
title: "Losing video on FE and config screens on BE"
date: 2012-12-05
forum: Mythbuntu
---

### Post by Anaximander Thales on 2012-12-05
I have recently started use MythTV.  After a few trials and tribulations that I have figured out on my own, I have become stumped and have not been able to find answers on this (Still learning terminology for Myth and hacking away at things, so it may be easier to find than I think).

I initially thought this issue would go away with an upgrade, but it hasn't -- so, I believe this started when I made some changes in the Front End with themes (this is a guess at my best recollection of when I started seeing this, and it's been a while).

I have an A75F-M motherboard, and am using the integrated ATI graphics processor only (out through HDMI only).  At boot the FE starts automatically.

So, here's the problems I'm running into --
1)  After closing (esc) out of the front end, if I start it back up, I can not see any video.  It does not matter if I attempt to watch live tv, recordings or videos, there is no video.  Audio plays, but I am shown 'please wait ...'  If I reboot the machine, then I get audio and video.

2)  If I attempt to make backend changes, I am unable to see any of the configuration screens except for System Events and Channel Editor.  What is odd about this is that the I-bar appears in areas where text should be entered, but all that is shown is the menu list (General, Capture Cards, Video Settings, etc.).  Rebooting does not solve this (I may attempt to stop the FE from starting at boot and see if that resolves the issue).  In the past, sometimes a wait has resolved it, but that's been upwards of 30 minutes.

At this point, I am up to date on all packages.  I have looked through log files, but am unsure of what is important to this.  Other than these issues, everything else seems to run fine.

Does any one have any ideas on this?

Thanks
AT

---

### Post by nickrout on 2012-12-05
Try a different ui painter. There is opengl and (ummm) another one I can't recall the name of.

---

### Post by Anaximander Thales on 2012-12-05
That was it -- seems so simple now, but, when you rack your brain sometimes simple is lost on you.

thank you very much.
AT

---

