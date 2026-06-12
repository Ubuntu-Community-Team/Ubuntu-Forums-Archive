---
title: "Motion w/Logitech C720 low resolution in YUYV"
date: 2012-12-15
forum: Multimedia Software
---

### Post by ub-newbie on 2012-12-15
Posting this so I can find my solution later.

OS - 10.04 LTS 32bit Desktop

Problem:  Start using my Logitech C270 with Motion 

Symptoms:  ```
luvcview -L
``` shows compatible modes of:
[LIST=1]
[*]YUYV, but max resolution is 176 X 144
[*]MJPG, but I get "Does not support read i/o" and image data is garbled
[/LIST]

Test/Verify: (all were sucesfull)
[LIST=1]
[*]luvcview -L
[*]luvcview -d /dev/video0
[*]gstreamer-properties
[*]Cheese
[/LIST]

Solution:
    I gave up on Motion and installed ZoneMinder.  Couldn't get ZM working.  I re-ran "luvcview -L" and VIOLA... Lots of new modes appeared under YUYV.  So I now have Motion running at 1280 X 720 with my Logitech C270.  I don't know what fixed it, I just know that it's fixed.

**[UPDATE]** It didn't survive the reboot...  Tried to install "QC-USB-SOURCE" but it is a little over my head.    If anyone know how to mark this as "unsolved" please let me know.

**{UPDATE 2}** After hours of work, it looks like the C270 will NOT work with Motion at any resolution except 176 X 144 .  Tried it on 10.04 & 12.04, same results.  I have the 1280 X 720 files to antagonize me, but I never got it working again.

---

