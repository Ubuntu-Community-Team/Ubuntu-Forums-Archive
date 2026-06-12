---
title: "Surround Sound with GT430"
date: 2012-04-01
forum: Mythbuntu
---

### Post by Em0ry42 on 2012-04-01
Hi,

I installed Mythbuntu 11.10 last night with my GT430 on my Asus P5N-e SLI and I'm getting stereo sound via the HDMI cable into my receiver but no 5.1.

Opening alsamixer doesn't reveal a whole lot of options to me.  Basically all I can do is unmute channels (which I've done).  I'm a bit of a n00b when it comes to audio issues, so any assistance would be appreciated!

Let me know what additional information you need!

---

### Post by nickrout on 2012-04-01
What sound does your source material have? Is it stereo or 5.1 or what?

make sure you have the right device chosen in mythtv (frontend) setup. Make sure you scan for devices then go through them and choose what looks right.

---

### Post by Em0ry42 on 2012-04-02
Thanks for the response! Figured it out last night:

Apparently I basically just needed one more reboot.  I was tipped off by a thread asking about the contents of /proc/asound/card1/eld#3.0

When I looked at this file I realized my receiver may have been reporting only 2 channel capability.  Changed the receiver settings and rebooted and ta-da!  Glorious 5.1 sound!

---

