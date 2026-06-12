---
title: "Can not get Hauppauge PVR-150 to work in VLC GUI"
date: 2013-12-26
forum: Multimedia Software
---

### Post by pactaman on 2013-12-26
Not sure whats wrong, loaded all required drivers, changed input via v4l2-ctl -i 2(composite) but i cant seem to get VLC to play anything off the card. When I open the wizard it recognizes /dev/video0, i pick NTSC and leave frequency empty. VLC loads, time starts to count but video doesn't change and all I see is VLC's traffic cone.
Do I need to change anything within ivtv?

If I try to dump the input through cat /dev/video0 > test.mpg it works fine and I see the contents of the input.

Any ideas what I am doing wrong?

---

