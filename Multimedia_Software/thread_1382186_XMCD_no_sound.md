---
title: "XMCD no sound"
date: 2010-01-15
forum: Multimedia Software
---

### Post by belgianfries on 2010-01-15
After being annoyed by most major mutimedia apps being unable to conveniently playing plain old audio CDs, I had a sudden epiphany and remembered that there was XMCD, which always worked well for me in the past. An "apt-get install xmcd" did the trick to get it installed and it still works just fine - but no sound!
Can anyone here help an old Linux user to get XMCD to play my Depeche Mode CDs again?

I am using 9.10 BTW. Sound works just fine on my BenQ Joybook S73G, which has some Intel sound as far as I could figure out.

Don't tell me I am missing the cable between the CDROM drive and the soundcard, please...

Cheers,
Torsten

---

### Post by Corin-EU on 2010-02-02
> **BelgianFries said:**
> Don't tell me I am missing the cable between the CDROM drive and the soundcard, please...
XMCD introduced CD Digital Audio (CDDA) by digital audio extraction (DAE) with version 3.1 for GNU/Linux systems.

The most recent version of XMCD is 3.3.2 of April 2004.

Ubuntu 9.10 provides XMCD version 2.6 (the last of the version 2 releases) from February 2000, therefore you will not get any sound on your sound card without an audio cable.

So if you really do have a audio cable without an electrical break in it going 

a) from the CD-rom analog output to your sound card, then you need to adjust the CD-rom analog output level in alsamixer

or

b) from the CD-rom digital output to your sound card, then you need to adjust the SPDIF / IEC958 output level in alsamixer

If you have PulseAudio up and running as your default sound device, then you will have to point alsamixer to your actual sound card with

alsamixer -D hw:0

---

