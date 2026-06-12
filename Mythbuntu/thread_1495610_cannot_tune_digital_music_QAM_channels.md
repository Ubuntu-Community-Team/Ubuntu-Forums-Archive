---
title: "cannot tune digital music QAM channels"
date: 2010-05-28
forum: Mythbuntu
---

### Post by bcg30506 on 2010-05-28
I have the HDHomeRun setup and working great in mythtv 0.21 with one exception.  The digital music channels Charter provides will not tune in mythtv.  With Live TV, the frontend goes to the playback failed screen and the recording file is 0 bytes.  If I schedule a recording of one of these stations and play it back later, the file is there and I can see and hear it, but it is too fast.  An hour recording shows as one minute.

When I use hdhomerun_config_gui to tune any of them and view (which brings them up in VLC) they are perfect, just as they look on a charter digital cable box direct to the TV.

So it seems to be specific to mythtv and not the tuner.  All other QAM channels tune and playback fine.  The logs aren't helping me but I can post if they would help.  I just need to know what switches to use.

---

### Post by Lepy on 2010-05-28
I used to be unable to tune comcast digital music channels, but now they work. I'm afraid I won't be much help because I can't remember if I made any config changes or if the v4l drivers were update for my particular card.

You might try disabling quick tuning or modifying your channel frequency table.

---

### Post by bcg30506 on 2010-05-28
I already had quick tune off.  I do not know what to change the frequency table to.  It matches what hdhomerun_config_gui says that vlc plays fine.

On the playback issue, I have 2 sample mpg files that mythtv did record from the music QAM channels using the schedule but it cannot play them back correctly.  Mplayer does the same thing as mythfrontend.  ffplay plays them both back perfectly.  Even as short as they are, they are probably too large to attach here.  Anyone know the max upload size?  If anyone wants to view them to see what I mean, I can either attach or put them on a server somewhere.

---

