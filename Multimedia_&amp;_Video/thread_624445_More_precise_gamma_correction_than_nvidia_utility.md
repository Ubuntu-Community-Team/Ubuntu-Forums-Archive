---
title: "More precise gamma correction than nvidia utility?"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by cjv998 on 2007-11-27
Hi everyone, I've came across a problem I have with Ubuntu (7.10 specifically).  In Windows, I could use my Nvidia driver software to calibrate gamma very well...I mean, more so than just adjusting the value for each color, I could go into each color's gamma curve and adjust individual sections (you could click on the gamma curve to create a point on it, and then drag the point to alter the curve's shape...hopefully someone understands what I'm talking about, I may boot back into Windows later and grab some screenshots).  I can't seem to do this in Ubuntu...so does anyone know of a more accurate/precise gamma correction utility than the nVidia drivers?  (It seems that's all xgamma can adjust as well, but maybe I'm wrong.)

Edit: Here's a screenshot of what I'm talking about; I'd like to be able to do this in Ubuntu.

Edit #2: Never mind, I'm reasonably happy with the results I got from messing with xgamma through Ubuntu's normal nvidia drivers.  I just had to do some calculations to figure out what I had to set it to in order to get a final gamma of 2.2 (I used one of those grayscale color calibration charts to determine my initial gamma, which ended up being around 2.5-2.6.  Then I divided my desired gamma of 2.2 by the initial number to get my scaling ratio ( ~ 0.8 ), which I put into nvidia's xgamma front-end, and voila! Final gamma of approximately 2.2).  I realize I shouldn't expect the same picture quality from my monitor (Hanns-G 19" widescreen LCD) as I'd get from a several-hundred dollar CRT, although it does look quite nice for being a cheaper LCD panel, and I'd definitely recommend it.

---

