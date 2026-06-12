---
title: "SPDIF problem with 2 different cards"
date: 2011-06-09
forum: Multimedia Software
---

### Post by goras on 2011-06-09
I have 2 sound cards each one with one problem. I connect both to a external decoder via SPDIF.

Here is my alsa-info output: [http://www.alsa-project.org/db/?f=6b86fe0e8559474b21fa423f7eb8f1a59879a6ca](http://www.alsa-project.org/db/?f=6b86fe0e8559474b21fa423f7eb8f1a59879a6ca)

_**Card1: Audigy 2 Value**_
- [COLOR=Red]When I try to passthrough AC3 or DTS audio to my decoder I get an horrible cracking sound.[/COLOR] I do this with mplayer + alsa since pulseaudio doesn't support AC3 passthrough yet.
- [COLOR=Lime][COLOR=SeaGreen]If I try to play multiple sounds using alsa it works[/COLOR].[/COLOR] For example opening 3 different videos with mplayer + **alsa** to the same device, I get to hear all the 3 audios at the same time.

example:
mplayer -ao alsa:device=hw=0.0 -ac hwac3 video1.avi
mplayer -ao alsa:device=hw=0.0 -ac hwac3 video2.avi
mplayer -ao alsa:device=hw=0.0 -ac hwac3 video3.avi

**_Card2: Built-in Realtek ALC883_**
- [COLOR=SeaGreen]When I try to passthrough AC3/DTS audio to my decoder it works (with mplayer + alsa).[/COLOR]
- [COLOR=Red]If I try to play multiple sounds using alsa it doesn't work.[/COLOR] I get this error:
[AO_ALSA] alsa-lib: pcm_hw.c:1293:(snd_pcm_hw_open) open '/dev/snd/pcmC1D1p' failed (-16): Device or resource busy
[AO_ALSA] Playback open error: Device or resource busy


Any one with ides on how to solve at least one of the problems so I can use one card fully?

Thanks

---

### Post by BicyclerBoy on 2011-06-10
Firstly I have not looked at your alsa setup info.
I'm happy to be proven wrong about anything.

Clarify digital pass-thru S/PDIF IEC958:
It is non-HD.
Used for AC3 & DTS
You can not share the digital pass-thru device i.e. multi-channel AC3(a52) & DTS.
You can share/mix/volume-control the S/PDIF output for 2ch stereo PCM.

So Card2 is working correctly.
Card1 setup must be outputing PCM or broken AC3.
Card1 multiple mplayer must be PCM.

I don't think your mplayer invocation is correct..-ao *alsa*:device=*iec958* or
mplayer -ao alsa:device=spdif -ac hwac3 test.mpg

it is possible the mplayer ac3 encoder is broken.
Your asound.conf needs something similar for your audio device
pcm.!default {
  type plug slave {
    pcm "spdif"
    rate 48000
    format S16_LE
  }
}

The actually rate can be up to 192KHz but most soundcards (& audio receivers) can't do it.

I have heard that Pulseaudio is almost working with digital pass-thru' but this still will not allow sharing/mixing...

Only shared digital pass thru' soln:
If you want to use multi-channel digital pass-thru AC3 with sharing/volume/mixing you have to use the alsa a52 plug-in & a mixer device.

A52 plug-in:
I have used a52 plug-in with channel re-ordering (but not sharing) but it will not compile with alsa 1.0.24.
I have found that the a52 plug-in causes problems after 1hr (fixed by pause/play).
The audio quality is not right.

---

### Post by goras on 2011-06-10
Thank you for you reply!

About Card2 and multiple sounds, the problem is with normal PCM stereo sound. i.e. a normal avi movie with mp3 stereo sound.

I'm not trying to encode streams to AC3, just to passthrough.

What's the pcm.!default stuff for?

---

### Post by BicyclerBoy on 2011-06-11
There is nothing normal about .avi container.

With the Card1 example you are asking mplayer to encode/copy to AC3 so I assumed.
mplayer -ac hwac3,hwdts,

With Card2 ..alsa does not support sharing/multiple playback without some mixer tricks..dmix (output) & dsnoop (inputs) plugs.
You output to an alsa dmix plug & this connects to other plug (You have to find your soln..see the alsa project website wiki.).
Note this will not work for AC3 DTS. Only alsa a52 plug-in can do that  (AC3 only).

Pulseaudio makes this easier.

Just set your system wide sound preferences to pulse & over-ride it with individual app settings as needed.(AC3 & DTS)
One good feature of S/PDIF pass-thru' is that the link is closed when you pause or stop playback so some other app can output over the same output device.

That asound.conf stuff was an example of what is needed to get digital pass-thru' AC3 & DTS working on many systems in the past...I think it just default now so ignore it.

---

### Post by jocko on 2011-06-11
From what I can see on [Alsa's support matrix]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs"),  the Audigy2 value has full hardware mixing support, which is why it can play more than one analog sound at once, but apparently it  does not support all rates (only supports 48 kHz)... Maybe the files you try to play have some other rate? That usually ends up sounding like an old analog modem... You should see in mplayer's output what rate the sound stream have.

The realtek card seems to be working perfectly fine. It has no hardware mixer, so if you need to hear sound from more than one application at once you neet to use a software mixer. Either use pulseaudio or set up a software mixer in alsa...

---

### Post by BicyclerBoy on 2011-06-11
I did not realise the "real" soundcard had a h/w mixer supported by alsa..
That explains how Card1 could support multiple alsa outputs.

So there is still some very small reason to have a soundcard. Pity about the 48KHz limitation.

---

### Post by goras on 2011-06-11
Newbie questions follow:

So, with the onboard card (card2), I can't get 2 sounds at once because it doesn't have a hardware mixer? and you know this by looking at the alsa-info stuff I posted?

Then, in windows, I'll probably have the same problem with card2 right? I'll only be able to play 1 sound at once? or windows uses SW mixing?

So ppl using their onboard cards. ALC883/888 have this problem too (can't play more than one PCM stream with alsa) ? this sucks!


EDIT: about card1 and it's problem, in windows I can set the SPDIF rate to 44/48/96KHz and works fine, even with the same file that in ubuntu I get the modem sound.

EDIT2: The file I'm trying to passthrough is 48KHz: Audio: Dolby AC3 48000Hz 5ch 448kbps [Audio 1].

Thanks for your replies guys!

---

### Post by BicyclerBoy on 2011-06-11
Having a h/w feature & having it supported & working are (3) different things.
Alsa does not (probably can not) support all h/w fully.

You can configure alsa to be a software mixer...but it is easier to just let pulseaudio do this because it defaults to this anyway.

48KHz & digital pass-thru' working (IF this is the case!) is not a bad status.

Card1.
I think your mplayer cmdline options were wrong..but I'm not clever enough to know what it should be..

That horrible noise you hear could be caused by the fact that digital-pass thru' does not work on that hardware.

Have you tried
speaker-test  -D iec958 -c2
vlc --aout alsa --alsa-audio-device iec958
& then play some AC3 audio track...

When it or you crashes just close the terminal session & re-open..

Can you install run
pavucontrol
Is your card 1. listed with a S/PDIF device ?

---

### Post by goras on 2011-06-12
I've attached the screenshot

---

### Post by BicyclerBoy on 2011-06-13
All I can suggest is checking with
alsamixer
pavucontrol

Check that all the S/PDIF vu's are not muted & set to max 100% level

The digital pass-thru' AC3/DTS requires bit perfect data transfer & 48KHz rate.
Maybe you have to force the rate in asound.conf...
speaker-test can not test dig pass-thru' only PCM or analogue multi-channel.

I have seen that Windows users of this soundcard have to use program called "spdifer" to make this work.

Just use the on-board with pulseaudio default output device & override to alsa iec958 in mplayer for DVD etc.....

---

