---
title: "ffmpeg output settings advice"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by Yleeyas on 2007-08-16
I've been using ffmpeg  to convert flv to mpg with good success on the smaller files (eg; 320x240). There is minimal or no deterioration of quality. However today I converted a good quality flv file (720x480) to mpg using:

ffmpeg -i a.flv -ab 56 -ar 22050 -b 500 -s 720x480 a.mpg

and noticed a marked degradation of the picture; the picture seems 'patchy', watchable but not as good as the source.
I've checked the man pages and played with some of the parameters but I thought someone could point me at which parameters to fiddle with to improve the resolution. Or if you could point me at an ffmpeg user primer:)

tia
yleeyas


edit:
Ok, nevermind.
 I get it; bitrate = resolution.

---

