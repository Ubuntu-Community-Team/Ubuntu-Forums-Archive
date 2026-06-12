---
title: "Dell E773p monitor &amp; Intel Extreme Graphics 2 problem"
date: 2006-02-05
forum: Multimedia &amp; Video
---

### Post by psyke83 on 2006-02-05
Hi,

I'm having trouble with my Dell E773p monitor on my machine (Dell Dimension 1100, Intel Extreme Graphics 2/82865G). I have two problems. 

1. I cannot display 1024x768 or 640x480 under X.org; when I start X in 1024x768 the monitor displays the middle of the screen alone with an unusual mode reported in the monitor's menu (NEW MODE  70K / 87 HZ). The monitor settings can be adjusted to display the entire screen, but this is unacceptable, as when I reboot to Windows, the screen layout is messed up due to those adjustments. When I try 640x480, I also get a strange mode listed in the monitor config (NEW MODE  45K / 86 HZ), and although the entire screen is visible, if I adjust the mode to use the entire screen, Windows will be misconfigured when I use 640x480 too.

2. Two resolutions seem to work fine, 1280x1024 and 800x600, but only the latter mode respects the monitor's horizontal sync rate in the Xorg.conf. 1280x1024 will only display in 60Hz mode which is unacceptable.

There is no satisfactory resolution in which I can run X.org, so can someone please help with these issues? I'll attach my X.org config/logs if requested. I'm running Kubuntu Dapper (I've tried the Breezy LiveCD and the same problems occur).

Regards
psyke83

---

