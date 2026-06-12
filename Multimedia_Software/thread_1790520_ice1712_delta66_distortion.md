---
title: "ice1712 delta66 distortion"
date: 2011-06-25
forum: Multimedia Software
---

### Post by phase42 on 2011-06-25
I have done a fair bit of searching on this without finding anything to address it.  Have been using Ubuntu and many other distros before that for a long time.  My audio hardware is a Delta 66 card.  Works fine in Ubuntu 10.10 and earlier versions, but sound is distorted, noisy and full of wow and flutter using 11.04.  Have tried booting the Live CD to test and after:

amixer set 'DAC',0 127
amixer set 'DAC',1 127

so I get some sound, running the audio test produces the same heavily distorted signal.  Setting lower levels just produces the same distortion at lower amplitudes.

Sound quality is the same whether I use jack, or just let everything default to the out of the box settings.  Have tried several audio players - all with the same result.

While this is far more than a latency issue, I have also installed a low latency kernel with no change in quality.

If anyone has a Delta 44 or 66 working nicely under 11.04, please advise on how you achieved it.

thanks
Brian

---

