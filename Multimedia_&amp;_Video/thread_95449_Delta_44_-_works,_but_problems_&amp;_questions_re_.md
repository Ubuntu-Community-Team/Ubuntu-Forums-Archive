---
title: "Delta 44 - works, but problems &amp; questions re jack, ice1712, low latency kernel"
date: 2005-11-26
forum: Multimedia &amp; Video
---

### Post by reuben on 2005-11-26
Hi, I just got up and running with an M-Audio Delta 44. Awesome card, but I have some questions.

Here's how I got setup:
0) Ubuntu automatically detected the card, and enabled the ice1712 driver. Slick!!!
1) I installed envy24control using the instructions here: [http://ubuntuforums.org/showthread.php?t=7285](http://ubuntuforums.org/showthread.php?t=7285)
2) I installed QJackCtl from ubuntu repositories to start jack easily
3) I selected Jack output driver from xmms (I think I had to install xmms-jack)
4) I took channels 1 & 2, connected them to a stereo RCA cord, and put that into my mixer. Nice sound! :) 

Problems/Questions:
1) I cannot find the magic settings (e.g. in XMMS) to get ALSA output working without jack. (This is fine, because I can output to my motherboard soundcard using ALSA. However, it'd be nice.)
2) I would like to DJ with this. I would have two instances of XMMS running, one outputting to channels 1&2, one outputting to channels 3&4. However, when I try to do this (using the jack driver), XMMS complains that the sound card is being used. How can I set this up?
3) Xruns -- I get output like this (and corresponding sound glitches) when I switch windows, etc:
[I]
**** alsa_pcm: xrun of at least 18.086 msecs
**** alsa_pcm: xrun of at least 7.338 msecs
11:55:00.468 XRUN callback (2 skipped).
**** alsa_pcm: xrun of at least 6.931 msecs
11:55:26.625 XRUN callback (1 skipped).[/I]

I presume that I need to install a low latency kernel -- how do I go about doing this least painfully? I am running on an Athlon 64 (tho I'm using the 32 bit kernel, currently). Will using the low latency kernel impact normal use of the desktop? (I mostly use it to play movies, and do email & web.)

Thanks in advance for any help on this.

---

### Post by mathieujohnson on 2005-11-26
first of all.
It doesn't seem to be possible to run multiple xmms through jack.
well, at least not out of the box.
patching a kernel to get it to do low latency seems tedious and really hard (as far as what I read on the web).
But it is possible to just install the low latency kernel from the agnula distribution and all the associtated packages to get their low latency kernel running. (this is what I do for my recording studio, got 40+ ins and 40+ outs working!)
I am in the process of making a full how-to but in the meantime I sugest you download the demudi cd.
don't think there is a amd 64 version so stick with the 32bit version for now.
You will probably be able to make your dJ stuff with a second jack-aware audio app.
I beleive mplayer can play audio and it is able to output to jack, so this could be a possibility.

and about the xmms outputing to alsa, I can't make it run either, seems on my system nothing with alsa works, except jack, so I am really looking around for jack-aware apps or ways to get jack working on things.

and obviously, the x-runs will disapear with a patched kernel!
hope this helps

---

### Post by reuben on 2005-11-27
Thanks for the advice.

Do you have apt-sources for demudi? I'd rather just patch in via synaptic rather than download a cd.

---

### Post by reuben on 2005-11-27
Answering my own q:

 # A/DeMuDi stable
 deb [http://demudi.agnula.org/packages/demudi](http://demudi.agnula.org/packages/demudi) stable main

The kernels are available as:

kernel-image...multimedia
kernel-headers...multimedia

Will report back shortly as to efficacy.

---

