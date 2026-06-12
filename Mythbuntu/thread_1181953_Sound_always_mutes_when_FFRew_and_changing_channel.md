---
title: "Sound always mutes when FF/Rew and changing channels"
date: 2009-06-08
forum: Mythbuntu
---

### Post by bcg30506 on 2009-06-08
After upgrading the weekly build last weekend (9.04) my mythfrontend always mutes the sound when I start watching live tv or fast forward or rewind a recording or change channels.  I've attached a sample of the frontend log during the time that it occurs.  I've changed nothing in my setup and all was fine before the update to 1:0.21.0+fixes-20667-openglvdpau-0ubuntu0.

---

### Post by bcg30506 on 2009-06-08
I just upgraded to the latest weekly, 1:0.21.0+fixes-20674-openglvdpau-0ubuntu0 and it seems to have fixed this issue.  I know there were supposedly no changes except compatibility with the new nvidia 185 drivers, but all I can say is the sound plays without muting now when watching TV or FF/Rew a video.

Although, I still get the "Mixer unable to find control Master 1" messages in mythfrontend.log every time I change volume or seek within a file. Doesn't appear to harm anything.

---

