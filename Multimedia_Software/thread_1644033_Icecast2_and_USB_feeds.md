---
title: "Icecast2 and USB feeds"
date: 2010-12-12
forum: Multimedia Software
---

### Post by bon_the_one on 2010-12-12
Hello Again Everyone,

Hope you are all well, and in advance here are best wishes for a Good Christmas! xx

I have a problem I hope someone can help me with. I have an Ubuntu Server 10.10 install which I've connected a USB output from a mixing desk to. The desk shows up in Ubuntu as [08bb:2902 Texas Instruments Japan PCM2902 Audio Codec] in lsusb.

I've had a play with alsa, and I've got arecord capturing from the USB feeb at any rate I like, from 44,100 to 48,000. Anything lower is not good.

I need to get icecast2 to pick up the feed in from the USB device, which I have the hw details for, and send them out in an 128k MP3 stream and a 128k OGG stream. I would like to make the streams available on 9001 and 9002 for example, and use them in different ways, but I can't work out the recipe for icecast2.

Can anyone please give a few mins to tell me the conf I should be using to capture from a digital USB stream and send it back out to OGG and MP3 on different ports?

MANY thanks,

Bon.

---

