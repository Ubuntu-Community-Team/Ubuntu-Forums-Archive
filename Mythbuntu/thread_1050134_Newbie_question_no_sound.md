---
title: "Newbie question: no sound"
date: 2009-01-25
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-01-25
I'm making good progress, as a complete Linux newbie, setting up my Mythbuntu box, but the big problem is that I have no sound at all. I've tried unsuccessfully getting sound over HDMI, and posted a separate thread on that.

I've now tried connecting up my surround sound speakers via a coax S/PDIF connector. No sound at all. Nothing.

I assume there must be some option somewhere where I need to tell the system to output sound via the S/PDIF, but don't know where to look. Any ideas?

Many thanks
NM

---

### Post by korgman on 2009-01-25
Please give me some specifics:

What version of Alsa?   "aplay --version"
What sound card? "aplay -l"
Also, try this "aplay -L"


The Mythbuntu sound setting are on page 3 of Settings->General.  We'll get you going.  Let's take a look at your settings from a terminal first.

---

### Post by NautiusMaximus on 2009-01-25
Many thanks for that, korgman. 

That turned out to be a lot easier to fix than I thought it might be. I went to the sound settings on page 3 of Settings->General, just like you said, and there was an option there set to "Alsa-default". I simply set it to "Alsa-spdif", and everything just worked!

Hurrah!

I've been working on this PC for a good many weeks now, and it's finally usable!

Still plenty of things to troubleshoot before it does everything it's supposed to, but I just watched my first home DVD in surround sound, and it was a real joy!

Thanks again
NM

---

