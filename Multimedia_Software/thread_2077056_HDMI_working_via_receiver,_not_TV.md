---
title: "HDMI working via receiver, not TV"
date: 2012-10-27
forum: Multimedia Software
---

### Post by sydbat on 2012-10-27
OK...here's my problem...

Everything HDMI works fine if I have it go through my receiver (HDMI from computer to receiver, then to TV) - full AC3/Multi-channel/5.1. However, if I connect it the other way (comp > TV > receiver), I only get the video portion, and an error on the TV about incompatible audio signal.

Why?

I have all my HDMI equipment connected to my TV (Sharp Aquos) with zero problems. Only my Ubuntu 12.04 will not connect without issue to the TV.

Video card is Nvidia. I know the card is good. Could it just be the TV not processing things correctly?

Thanks in advance.

---

### Post by sydbat on 2012-11-07
Bumpity bump bump...

---

### Post by BicyclerBoy on 2012-11-08
Your working hookup is the best arrangement.
HDA hdmi audio uses EDID data to report capability between devices..
Devices in the chain add data as it is passed back to source.

Are you using s/pdif over hdmi (pre-azalia) ?

The 1st gen graphics card did not have HDA codec on-board but just relayed the mobo spdif over hdmi.
This limited them to stereo & AC3/DTS & no capability reporting.

AFAIK TVs only output AC3 from internal digital tuner & they don't transcode but anything is possible.
The TV's error message that your PC is outputting an in correct audio format & suggests s/pdif or bad EDID reporting.

The hdmi ARC could be used to allow TV to output thru' AVR HTamp & retain your working connectivity soln

---

### Post by sydbat on 2012-11-08
Thanks for your reply.

Yes, all audio and video go through the HDMI. The card is Nvidia GT220.

I imagine that the TV is doing what you suggest - telling me that the EDID is not right, even if it is. If my TV were a couple of years newer, I likely wouldn't have this problem? The HDPVR works flawlessly through HDMI to the TV, and it is a few years older than my video card. Weird.

I'll have to keep things set up as they are for the time being. I like the fact that I get true surround through the amp (only a year or so old). I'd hate to lose that just for the convenience of running everything through the TV > amp.

Thanks again.

---

### Post by BicyclerBoy on 2012-11-08
The GT220 is a real HDA audio device so should support EDID etc..

You could have a look at the hot-plug events & the reported EDID files..
dmesg | grep HDA
aplay -l

- which card is the nvidia 0 or 1 or 2 etc ?..

Then search /proc/asound/card1/eld#* files..(assuming card1)

For ex: If hw:1,9 is your pin codec then the EDID data is in /eld#3.0.
Does eld#3.1 exist ?

Compare the eld file contents when you have the TV directly connected etc..

---

