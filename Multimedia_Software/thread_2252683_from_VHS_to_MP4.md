---
title: "from VHS to MP4"
date: 2014-11-13
forum: Multimedia Software
---

### Post by lift_test on 2014-11-13
Can you convert VHS tapes to MP4 in Ubuntu?  If so what hardware/software/leads do I need (I do have a VHS player)?

---

### Post by TheFu on 2014-11-13
Yes, you need a VHS player and some sort of capture device. 
I don't use Linux for this myself ( I use <cough> hauppauge capture devices and <cough> that other OS), I am embarrassed to say.

For capture cards, check the mythTV hardware compatibility, but you'll still need a VHS to play the video so it can be captured. VHS is not a digital format, so capture is the only way.

Generally the steps are:
* Connect the VHS player video to the capture card using the highest quality connector possible, svideo
* Connect the VHS player audio to the capture card using the RCA L/R stereo cables.
* Tell the capture card to record, then tell the VHS player to play the tape.
* Generally, the capture will be stored in MPEG2 format - this is easiest and probably in 640x480 resolution. This is slightly higher than VHS native resolution, so it will seem a little fuzzy.
* Use any program to cut the parts you don't want - avidemux would be fine.
* Then use any program to transcode from mpeg2 into whatever codec you want the mp4 container to hold - most of the time, that would be h.264, but for low resolution content, xvid/mp4 is probably more efficient for the same quality. avidemux can do that output.

Good luck.

---

### Post by lift_test on 2014-11-14
No need for embarrassment, sometimes another OS is preferable for a given task.  Thank you for the information.

---

### Post by FakeOutdoorsman on 2014-11-14
Here's my [workflow](http://ubuntuforums.org/showthread.php?t=2241631&page=2&p=13112340&viewfull=1#post13112340).

---

### Post by lift_test on 2014-11-14
> **FakeOutdoorsman said:**
> Here's my [workflow](http://ubuntuforums.org/showthread.php?t=2241631&page=2&p=13112340&viewfull=1#post13112340).

'Tis a fairly pricey bit of kit but looks good, I'll have to think about that one.  Thanks for the info.

---

### Post by FakeOutdoorsman on 2014-11-14
There are probably much cheaper and more modern alternatives than the ancient device I use to convert the analog signal to digital, but I haven't tried anything else.

---

### Post by lisati on 2014-11-14
Things might have changed in the last few years since I last tried one about 4 or 5 years ago, but my experience with capture cards was less than satisfactory.

These days I tend to use a DVD recorder with HDD, recording from VHS to HDD, then copying to DVD. I can then import the DVD contents to my computer to do any tidying up necessary. The model I have also has a firewire/iLink connector making it easier to use with two of my camcorders. 

I also have another machine, a combo DVD recorder/VCR, but the tape deck hasn't been the same since a dodgy tape got seriously snarled..... :(

---

### Post by lift_test on 2014-11-15
We only have a few family tapes but would like ensure they are viewable for as long as possible.  VHS tapes are notorious for deteriorating and snarling, also how long are VHS players going to be available?

---

### Post by TheFu on 2014-11-15
> **lift_test said:**
> We only have a few family tapes but would like ensure they are viewable for as long as possible.  VHS tapes are notorious for deteriorating and snarling, also how long are VHS players going to be available?

I have 3 here.  2 of them are not plastic and were considered high quality they required svideo and had metal parts.  I think at least another 20 yrs.

For what you want, the capture device should be $25-$50 - no more.  Just check the mythtv compatible cards that have non-TV inputs.  I have a Hauppauge 950Q and a Plextor something that claim support for Linux - just never used them.  The 950Q chips are extremely popular with many vendors of the USB2 tuner devices from a few different brands.

---

