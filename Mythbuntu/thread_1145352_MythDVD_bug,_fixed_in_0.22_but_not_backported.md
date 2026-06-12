---
title: "MythDVD bug, fixed in 0.22 but not backported"
date: 2009-05-01
forum: Mythbuntu
---

### Post by Dewey_Oxberger on 2009-05-01
There is a bug in MythDVD (0.21-fixes): it'll freeze at the copyright warning page (or some other page before the main menu) on a lot of Disney related videos (modern videos anyway).

The bug isn't in trunk - 0.22.  It went away in the sync with the new ffmpeg rev.  The fix can't be backported.

Any ideas on how to get around my dozen or so videos that won't play?

Is trunk a wild playground that I should avoid?

Should I just rewire myth to use some other player?

What have all you done to get around this?

---

### Post by AlecJ on 2009-05-01
> **Dewey_Oxberger said:**
> There is a bug in MythDVD (0.21-fixes): it'll freeze at the copyright warning page (or some other page before the main menu) on a lot of Disney related videos (modern videos anyway).

The bug isn't in trunk - 0.22.  It went away in the sync with the new ffmpeg rev.  The fix can't be backported.

Any ideas on how to get around my dozen or so videos that won't play?

Is trunk a wild playground that I should avoid?

Should I just rewire myth to use some other player?

What have all you done to get around this?

Yep! you press the menu button or "m" on keyboard and select "DVD Root Menu" before it gets to the copyright page, so fast fingers, from there you can play movie..etc
If at first this won't work you have to reboot, ensure the dvd is mounted and try again. I know it's a bloody pain!

---

### Post by Dewey_Oxberger on 2009-05-02
I have several dvd's where that menu trick doesn't work - the menu shows the stillframe and it freezes.

I don't reboot when it happens.  I ctrl+alt F6, log in, sudo top, look for mythfrontend, then k its pid.  Then ctrl+alt F7 back to the desktop.  Faster  than  reboot.

---

### Post by AlecJ on 2009-05-02
I don't have a keyboard on my box as it lives under the TV so I'm stuck with the reboot from the on/off button. But that seems to get it to play.
I have been ripping the main movie from the DVD's with DVDfab on the windows box to the myth box over the network. I get the best results this way, no lockup's or freezing.

---

