---
title: "Latest video libraries updates causing problems."
date: 2013-01-29
forum: Mythbuntu
---

### Post by GuiGuy on 2013-01-29
I'm using mythbuntu with mythtv 0.25. Yesterday there was an update for what seemed to be  a bunch of video library files.

Today only the NORMAL and most basic of settinsg using ffmpeg for Settings > Video > Playback work on my system, one that was previously humming along very nicely. Attempting any other setting locks the screen when exiting the video. I then need to re-boot. 

Please note I am only venting here and I am looking around for a Window. 

Why do THEY do this to us all the time? Don't they test before releasing their latest malfeasance upon us unsuspecting clods?

PS: I have spent the best part of 12 hours trying to get on top of this, but no joy. All I get now is s s s t t t u t t t e r r r i n n g g g live TV.

:(

---

### Post by santosh83 on 2013-01-29
> **GuiGuy said:**
> I'm using mythbuntu with mythtv 0.25. Yesterday there was an update for what seemed to be  a bunch of video library files.

Today only the NORMAL and most basic of settinsg using ffmpeg for Settings > Video > Playback work on my system, one that was previously humming along very nicely. Attempting any other setting locks the screen when exiting the video. I then need to re-boot. 

Please note I am only venting here and I am looking around for a Window. 

Why do THEY do this to us all the time? Don't they test before releasing their latest malfeasance upon us unsuspecting clods?

PS: I have spent the best part of 12 hours trying to get on top of this, but no joy. All I get now is s s s t t t u t t t e r r r i n n g g g live TV.

:(

Hmm I don't have any experience with Mythbuntu (or mixing the PC and the TV for that matter), but clearly, a mechanism to roll-back updates is wanted. If updates can break stuff even on LTS releases then folks on normal releases will find such a roll-back tool even more useful.

And one doesn't have to stop updating permanently; just long enough so that the developers notified of the bug get the time to fix it. I also read on another site that regression was one of the biggest problems in Linux.

And I think even Windows has uninstall for updates if I remember correctly.

Creating a full-system snapshot before every little upgrade is probably not even remotely feasible for most users.

---

### Post by GuiGuy on 2013-01-29
> **santosh83 said:**
> 
And I think even Windows has uninstall for updates if I remember correctly.

Creating a full-system snapshot before every little upgrade is probably not even remotely feasible for most users.

Thanks for the comments. Windows does do roll backs as you say. I do have backups, but that is not the point. An update for an LTS version should not break a user's setup that is reasonably vanilla and on established hardware.

---

### Post by GuiGuy on 2013-01-30
These are the files that were updated. One or more of them killed my mythbox :(

> 
apport evolution-data-server evolution-data-server-common ffmpeg libav-tools
  libavcodec53 libavdevice53 libavfilter2 libavformat53 libavutil51
  libcamel-1.2-40 libebackend-1.2-5 libebook-1.2-14 libecal-1.2-15
  libedata-book-1.2-15 libedata-cal-1.2-18 libedataserver-1.2-17 libpostproc52
  libssh-4 libswscale2 python-apport python-problem-report python3-apport
  python3-problem-report


---

