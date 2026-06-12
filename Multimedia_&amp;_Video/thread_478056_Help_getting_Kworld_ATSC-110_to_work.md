---
title: "Help getting Kworld ATSC-110 to work"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by Nicolae on 2007-06-18
I've gotten a Kworld ATSC-110 card, and I'm having a hell of a time trying to get it to work. I've searched around on the forums, but nothing I've come across has helped. First issue: I get nothing trying to tune QAM channels in ANYTHING. scan gives me about 30 channels, azap can lock them, and dvbsnoop is showing that they're broadcasting some kind of data, but mplayer/xine can't read them. I've a feeling that, unfortunately, this means they're all encryped (damned comcast), but I was wondering if there's anything else I can try.  I also can't get analog tv in mythtv at all. It tunes the channels for about 2 seconds, then drops to a black screen. No audio, either. Not a clue what to do about that. I'm pretty sure the cable is on the right jack, as I get nothing with it hooked into the other one. 

Here's my channels.conf I end up with, dunno if it's indicative of encrypted channels, or...
```
[000-0001]:621000000:QAM_256:64:65:1
[001-0004]:621000000:QAM_256:68:69:4
[002-0014]:627000000:QAM_256:64:65:20
[003-001e]:627000000:QAM_256:67:68:30
[004-0032]:627000000:QAM_256:77:78:50
[005-0046]:627000000:QAM_256:74:75:70
[006-0050]:627000000:QAM_256:72:73:80
[007-0001]:699000000:QAM_256:0:65:1
[008-0001]:705000000:QAM_256:0:65:1
[009-0003]:705000000:QAM_256:0:77:3
[00a-0013]:705000000:QAM_256:0:80:19
[00b-0005]:705000000:QAM_256:0:68:5
[00c-0007]:705000000:QAM_256:0:84:7
[00d-0009]:705000000:QAM_256:0:89:9
[00e-000b]:705000000:QAM_256:0:75:11
[00f-000d]:705000000:QAM_256:0:82:13
[010-000f]:705000000:QAM_256:0:73:15
[011-0011]:705000000:QAM_256:0:91:17
[012-0015]:705000000:QAM_256:0:93:21
[013-0017]:705000000:QAM_256:0:97:23
[014-0019]:705000000:QAM_256:0:95:25
[015-001b]:705000000:QAM_256:0:99:27
[016-000a]:723000000:QAM_256:0:68:10
[017-0006]:723000000:QAM_256:0:73:6
[018-0002]:723000000:QAM_256:0:65:2
[019-0001]:723000000:QAM_256:0:77:1
[01a-0004]:723000000:QAM_256:0:83:4
[01b-0005]:723000000:QAM_256:0:80:5
[01c-00c9]:735000000:QAM_256:64:65:201
```

---

### Post by Nicolae on 2007-06-19
Um, ok. The card is not using the bottom input for... anything. ATSC, NTSC (cable and ota analog), and QAM are all going through the top input. 

I get some ATSC locks, but i don't expect good locks atm because I only have a pair of rabbit ears hooked up. 

Cable works in mythtv and vlc, but I get no sound. (I did the v4lctl commands listed on the card's page on the mythtv wiki to no avail)

Still not getting any QAM signals, except for the above. Still, even if every last QAM signal is encrypted, shouldn't I still be able to detect them? I know comcast offers about 300 digital channels in this area.... At this point, though, if I can get ATSC and NTSC on seperate inputs I'll be happy, I know from having had an ATI TV Wonder 650 I can get almost all the major broadcasters in the area with a bettter antenna...

---

### Post by modorf on 2007-06-20
I'd suggest reading this thread for some suggestions on help with KWorld ATSC-110 :: [http://ubuntuforums.org/showthread.php?t=372635](http://ubuntuforums.org/showthread.php?t=372635)

for no sound from cable :: verify that you have module saa7134-alsa loaded.

---

### Post by Nicolae on 2007-06-20
I've gotten the sound to work, actually. I needed to set myth to use /dev/dsp1 and set the sampling rate to 32000Hz.

And I've read through the thread, didn't find anything of use. Thanks, though.

I did get the ATSC and NTSC on seperate inputs as well, by recompiling the v4l-dvb drivers with a modification to the source. At this point, my only issue is the QAM, and I figure that's just Comcast encrypting everything :/

---

### Post by modorf on 2007-06-20
> **Nicolae said:**
> I've gotten the sound to work, actually. I needed to set myth to use /dev/dsp1 and set the sampling rate to 32000Hz.

And I've read through the thread, didn't find anything of use. Thanks, though.

I did get the ATSC and NTSC on seperate inputs as well, by recompiling the v4l-dvb drivers with a modification to the source. At this point, my only issue is the QAM, and I figure that's just Comcast encrypting everything :/

Do you know what frequancey table your using for analog cable?
I live in Boston, MA and have Comcast.  Their using `us-Cable-HRC-center-frequencies-QAM256`

---

### Post by Nicolae on 2007-06-20
I've scanned with HRC, IRC, Standard, and the EIA-542 ones. I get hits on IRC and Standard cable (Exact same ones).

---

