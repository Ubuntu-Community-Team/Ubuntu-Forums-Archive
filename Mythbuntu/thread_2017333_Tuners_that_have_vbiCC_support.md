---
title: "Tuners that have vbi/CC support?"
date: 2012-07-05
forum: Mythbuntu
---

### Post by Mad_Professor on 2012-07-05
I'm looking for a new tuner.

I prefer a USB so I can pci-passthrough the port to kvm guest running mythtbuntu, but I do have room for one PCI-E tuner but it has to be dual tuner.

**It needs to be able to do NTSC and CLOSED CAPTIONS ARE A MUST since I'm hearing impaired.**

I've already tried out the hvr-950q, couldn't get it to work.
Also tried out hvr-1950, even though it works, no closed captions because no vbi support or v4l2-ctl support even though mythtv wiki says it does. [http://www.mythtv.org/wiki/Analog_Hardware_Encoder_Cards](http://www.mythtv.org/wiki/Analog_Hardware_Encoder_Cards)


What are my options?

---

### Post by jlp_engineer on 2012-07-06
Do you have VBI CC enabled in the backend setup?  

This is disabled by default due to the negative impact it has on the image stability of some of the older analog tuners.

---

### Post by Mad_Professor on 2012-07-07
Yes, but it doesn't matter if V4L2 can't see vbi devices if linux kernel doesn't have support for it. The 950q didn't work because myth backend couldn't get it to tune, even though it worked with sound in tvtime. I got the 1950 to work but no vbi and it wouldn't encode the CC using ivtv because of that.

Not too mention that mythTV seems to have issues with analog side of things.

Frankly I've given up on mythtv and linux and tv tuners. Poor hardware support for tuners, broken documentation scatter across the net and the ever evolving linux kernel dropping and adding support for tuners, making wikis and other things useless.

---

### Post by nickrout on 2012-07-08
goodbye and good luck.

---

