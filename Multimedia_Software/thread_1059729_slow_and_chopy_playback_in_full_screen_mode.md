---
title: "slow and chopy playback in full screen mode"
date: 2009-02-04
forum: Multimedia Software
---

### Post by bojcistv on 2009-02-04
I have HP 6820s laptop with the intel qore duo on 1,8 GHz, graphic card is ATI Radeon X1350. I work in Ubuntu 8.10.
I have a following problem. When I start to play any movie (i thought on any movie format - *.avi, mpeg, mkv etc)in any player (VLC, Mplayer, SMplayer, Gxine) in a full screen mode playback is bit slow and CPU work in highest level all the time during the playback in full screen mode. Everything seems fine when I increase size of playback window.
I have installed ATI catalyst center (i think 8.1 version, I have not tried newest 9.1 driver distribution). Everything have worked quite nice without any problems till the some day when those problems with the slow playback in full screen mode occurred. I haven't touch anything since I have installed ATI 8.1 driver for linux. Off course Compiz was in turn off mode.
This problem just occur and I have no idea what has happen....
If anyone have any idea or suggestion I would appreciate that 
Thanks in advance

---

### Post by bojcistv on 2009-02-04
No one to help me!

Hmmm!

Than is only solution return to windows....

---

### Post by redroad55 on 2009-02-04
I personally shy away from anything that is packaged with a "W" these days ..You know,Windows ,Wall Mart , and George "W"..Need I say more, switching to Windows is a bit dramatic wouldn't you say..I saw today a new ATI driver was listed with recommended downloads .. Maybe that will help ..Post back ..Best to you

---

### Post by rvm4000 on 2009-02-04
> **bojcistv said:**
> Everything have worked quite nice without any problems till the some day when those problems with the slow playback in full screen mode occurred.

What video output are you using?

Maybe you're using x11, which is slow.

In smplayer you can change the video output in Preferences -> General, try to use xv, is the fastest.

---

