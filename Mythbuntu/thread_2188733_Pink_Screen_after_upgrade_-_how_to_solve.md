---
title: "Pink Screen after upgrade - how to solve?"
date: 2013-11-18
forum: Mythbuntu
---

### Post by scott.a.purdie on 2013-11-18
Hi.  Just made some updates to my system.  Specifically:


[LIST]
[*]Upgrade MythTV from .26 to .27
[*]Upgrade Ubuntu / Mythbuntu distro from 12.04 to 13.04
[/LIST]

This was yesterday.  As info, cable comes into a HDHR then to the computer.  Signal is run from the computer via HDMI to the receiver.  HDMI again from the receiver to the TV.

Twice now (100% of the time), after turning on the receiver and the TV, the screen in "pink".  Not solid pink mind you, but rather as if you were looking thru a pink screen at the tv.  It's viewable from a functional standpoint but unacceptable for tv viewing.

Restarting the computer fixes the problem; Logging out and back in (without a full reboot) does not correct the issue.

Video card is on-board ATI 3200.  I am using native drivers.

Any thoughts on why this is happening and how to fix it?  I didn't see any related threads.

Thanks.

---

### Post by scott.a.purdie on 2013-11-18
As an update:

Describing the screen color as "pink" was over-simplistic.  To be more specific, white items appear pinkish (so white letters are now pink).  The rest of the screen can be more accurately characterized as greenish.

Doing some sleuthing:


[LIST]
[*]Restarting the mythbox sets the video colors to normal
[*]Logging out / in has not effect
[*]Unplugging / replugging HDMI cable to TV has no effect
[*]Cycling power on receiver has no effect
[*]Cycling power on TV immediately impacts the color (from good to bad, specifically).  So... aha!...hmmmm...
[*]Unplugging / replugging HDMI cable to mythbox fixes the problem
[/LIST]

So now I have some isolation, but still not sure what the culprit is.  My assumption is the operating system tweaked something since this is a new issue on an otherwise mostly steady 4yr-old system and the timing is 100% simultaneous with the upgrade.

Can anyone replicate or speak to something similar?

Thanks.

---

