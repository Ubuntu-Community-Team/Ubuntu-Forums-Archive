---
title: "[SOLVED] capture composite from NOVA-S"
date: 2008-10-06
forum: Mythbuntu
---

### Post by MartinusEx on 2008-10-06
Hi out there,

I using
Mythbuntu 8.04.1
Hauppauge NOVA-S

I went though this forum and found Ian's reply to a similar question but it focused on a PVR-500:

> If the PVR-500 supports composite in, you need to define a new tuner and set the input to composite 1.

So, go to mythtv-setup, TV cards, Add new capture card, Card Type "MPEG-2 encoder card (PVR-500)", Select Video Device 1, Default Tuner "composite 1".

The go to video sources and add a new source that points to the tuner you've just created. I imagine that you'll need to create a new channel that points to the video source you've just created.

Regards
Ian Dobson

note: This is all just theory, as I can test it here.

As far as I know the NOVA-S has no encoder for composite and s-video, thos should be done by the main cpu using a certain software (for windows)


I tried Ian's howto but to no avail.

I added a tuner as V4L-Card (so detected by mythbuntu)
(I also tried the mpeg decoder card)
I set up a video source and linked it to v4lcard0:composite and s-video. (I tried both inputs to be sure)

I use a VCR (PAL) to test the input but the screen does only show noise or stays blank.
Sometimes I can see the information bar in the lower third of the screen bat cannot read the text nor is there a picture.

Does anyone have used the composite input of the hauppauge NOVA-S?

Is there any obviously in the mythbuntu setup that I might have missed?

one distrubing thing is, when setting up the video source, it always lets me select the program grabber (which seems to be nonsense since there is only a video stream coming in) but nothing else, shouldn't there be some setup like the stream is PAL or NTSC or the like?
I don't understand that issue and would be happy for any information on this.
Even a link to a good information source would be great.

Excerpt of Ina's reply:
> I imagine that you'll need to create a new channel that points to the video source you've just created.

Probably this might be the problem, but I cannot follow Ian's thought in the vidoe source setup. How to do that there?

thx a lot in advance

---

### Post by ian dobson on 2008-10-06
Hi,

When you define a video source you need to link it to a tuner, from what I can remember there are Several defined for the PVR-500 (s-video,tuner). 

What you need to do is tell MythTV that the video source "X" is the card input s-video for your card.

Regards
Ian Dobson

If I get a chance I'll have a look at it tonight on my test box.
Are you sure the NOVA-S has an analog tuner?

Regards
Ian Dobson

---

### Post by MartinusEx on 2008-10-06
Hi Ian,
thanks for reply :KS

nope, the NOVA-S uses a conexant chip for sattelite programs an encodes mpeg directly.

The s-video and composite inputs seem to be directly connected to an ADC and do not pass an analog tunert to my best of knowledge.

Is there any one on the board who owns a nova-s to bring some light into the dark?

Thats why I worried about the video setup and channels.
Is MythBuntu able to handle raw video capture (as it seems to be) directly  or should i go for linux tv to try to get another tool to capture analog video (compsite1).

can't get that straight.

rgds

---

### Post by MartinusEx on 2008-10-06
Ian and all,

the standard way to set the input up using MCC was good enough.

I had a broken cable without knowing it.

Setting the NOVA-S up as V4L Card and linking it to a video source with no  program grabber was OK no channel setting needed.
Although it is confusing that the video source setup still shows all the elements of scanning for channels

all the best

Martinus

---

