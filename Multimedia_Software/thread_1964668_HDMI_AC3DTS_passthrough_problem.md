---
title: "HDMI AC3/DTS passthrough problem"
date: 2012-04-24
forum: Multimedia Software
---

### Post by Szellem on 2012-04-24
Hello,

I've got a problem with sending AC3/DTS data to my receiver through HDMI.

What works:
-listen to PCM music via HDMI
-PCM and AC3/DTS passthrough via optical S/PDIF connection
-multi-channel PCM output via HDMI

What doesn't work:
-when I start to play a movie with mplayer with AC3/DTS passthrough and my receiver is on, my receiver recognizes the data stream as PCM and plays a rythmical noise (probably the digital packets interpreted as PCM) on the speaker
-when I start my computer with the receiver turned off, start to play a movie then switch on the receiver, the receiver recognizes the sound format and it works perfectly. However, when I restart the movie or seek in it, the receiver recognizes the stream as PCM again, and gives only the noise. It doesn't get fixed if I turn the receiver off and on again, until the computer is restarted, that's why I suspect it's not only the fault of the receiver.

Hardware info:
-CPU: intel core i3
-Motherboard: Asrock H67M-ITX/HT
-I use the integrated sound and video cards.
-Receiver: Denon AVR-1312

Software info:
-Ubuntu Studio 12.04, but the symptoms were exactly the same with Ubuntu Studio 11.10.

I haven't attached any logs because I don't know what's needed and I didn't want to flood the post with irrelevant information.

Does anybody have any idea? Any help would be greatly appreciated.

Thanks in advance!

---

### Post by BicyclerBoy on 2012-04-24
Seems like it is related to a digital pass-thru' over HDMI bug in alsa..

AFAIK When you stop/pause/seek the iec958 (S/PDIF) device is closed reopened. There could be something illegal sent on (re)opening.. 

Can you not work around this by using multi-channel LPCM over HDMI?
There is no loss in quality if the s/w decoders are working.
The AC3/DTS decoders in mplayer should be okay, I have doubts about the DTS-MA decoder AQ.

There is a daily build ppa for snd-hda-intel kernel module etc..This might help with your problem, might not..
[https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily](https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily)

---

### Post by Szellem on 2012-04-25
Thank you for your reply!
I will try your suggestions.

DTS is not a problem any more, I've found a decoding setting in my receiver, DTS decoding can be forced with that and it works perfectly. I'll try it with DTS MA as soon as I can get any medium with it.
Unfortunately only DTS, PCM and Auto mode (which doesn't really work) can be set, no AC3.

---

