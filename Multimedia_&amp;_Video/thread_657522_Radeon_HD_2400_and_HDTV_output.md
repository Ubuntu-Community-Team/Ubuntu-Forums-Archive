---
title: "Radeon HD 2400 and HDTV output"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by Trancecoder on 2008-01-03
Hello! I would like some input on my dilemma. I am running Gutsy 64 and attempting to get X to work with my TV.

The video card is a Radeon HD 2400. I am using the latest fglrx (8.44 or Catalyst 7.12) driver, and I have tried the previous one as well. The TV, a Mitsubishi HDTV with 1080i max resolution, is connected using component via the card's 7-pin port.

All I can get the TV to display properly is a Modes setting of "640x480", which the TV sees as 480i. In text mode, the TV sees 480p as the resolution. With any custom modeline I get a screwed up image (the TV still seeing 480i) with the mouse cursor, strangely enough, being displayed properly.

Here are some files which may be of use:
[http://www.trancecoder.com/xorg-stuff/xorg-480-working.log](http://www.trancecoder.com/xorg-stuff/xorg-480-working.log) - Xorg log with 640x480 mode
[http://www.trancecoder.com/xorg-stuff/xorg-720p-bad.log](http://www.trancecoder.com/xorg-stuff/xorg-720p-bad.log) - Xorg log with 720p mode
[http://www.trancecoder.com/xorg-stuff/xorg.conf](http://www.trancecoder.com/xorg-stuff/xorg.conf) - my conf file with 640x480 enabled and 720p commented out

Any feedback at all is appreciated.

---

