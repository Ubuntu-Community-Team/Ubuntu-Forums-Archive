---
title: "convert digital to analogue"
date: 2011-01-13
forum: Multimedia Software
---

### Post by iitywygms on 2011-01-13
Hi all.

Could someone please tell me how to have alsa convert a digital sound stream to analogue before it is sent to the hdmi out?
I would like to modify asound.conf.  I do not have gnome as a desktop so I need to manually input the changes to asound.conf.
The reason I ask is.
I have sound going out of my acer revo to both spdif and hdmi.  The spdif goes to my receiver and I want digital passthrough for that. The hdmi goes to my tv and I need it to be analouge before it gets to the tv.
Right now, I get passthrough to both the spdif and hdmi.  (the tv is all static)
I want to have alsa convert the signal for the hdmi output only.
Thanks.
I am so close.

---

### Post by BicyclerBoy on 2011-01-13
HDMI does not support analogue audio..

Do you really mean convert from DD5.1/AC3 & AAC & DTS  to 2 ch PCM for the TV ?

S/PDIF only supports 2 ch PCM & matrix encoded AC3 DTS
HDMI can support above + multi channel LPCM + HD audio.

The TV likely supports the same (wasted on TV).

Sounds (pardon the pun) to me that the HDMI audio output is not working right & your TV does not like it.
Is it loud static or just cheap audio amp static ?

Video h/w ?
video driver version ?
Alsa version ?
aplay -l ?
aplay -L ?

---

### Post by iitywygms on 2011-01-13
> **BicyclerBoy said:**
> Do you really mean convert from DD5.1/AC3 & AAC & DTS  to 2 ch PCM for the TV ?  Yes, sorry about that.


> **BicyclerBoy said:**
> Sounds (pardon the pun) to me that the HDMI audio output is not working right & your TV does not like it.
Is it loud static or just cheap audio amp static ?
Loud static.

I am not home but I do have some info on hand.

aplay -L
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
Subdevices: 0/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0

I know that when I tell mythtv the speaker setup is stereo, sound will work through both hdmi and spdif.  Problem is, my spdif signal is no longer passthrough.
(I no longer get the "dolby digital" displayed on my receiver.)  Only stereo pcm.  Which means mythtv is converting/changing both signals.  I only want to "convert" the signal on the hdmi to the tv.
The tv is a panasonic plasma 54-s1

I will post my asound.conf and all the asked for info when I get home.
Thanks again.

---

### Post by BicyclerBoy on 2011-01-13
MythTV0.24 can do this directly by use of extra audio config stuff.

Quite a few people want something similar so they do not need the HT amp just for a bit of quiet TV viewing.
There was a recent post on mythtv.org (answered by the code author JYA) that detailed a very similar configuration setup.

[http://www.gossamer-threads.com/lists/mythtv/users/467508](http://www.gossamer-threads.com/lists/mythtv/users/467508)
post #10 has the solution.
This explains (with 0.24+fixes JYA) how to do what you want (I think).

 Anotherway to achieve this is using a custom mixer setup & select this in mythtv audio.
The mixer can handle digital & analog conversions.
You may need to mute the TV when using the HT amp (AVR)

---

### Post by iitywygms on 2011-01-13
I have been reading that mythtv mailing list thread.  They talk about using analogue out (rca) and digital Spdif or hdmi.
I want to use spdif and hdmi.  I have tried millions of combinations in the mythtv setup, and nothing did what I ask.
So, I would like to configure asound.conf to do it.  Then in mythtv-setup I will use alsa:default

---

### Post by BicyclerBoy on 2011-01-13
I edited my previous post with link to MythTV soln no alsa asound fiddling required.

The asound alsa stuff just/can screws up pulse & other apps.

If you use a custom alsa mixer then S/PDIF digital pass thru' (AC3 DTS) will not work.

If you use internal volume control (mythTV) digital pass thru' will fail.

---

### Post by iitywygms on 2011-01-13
> **BicyclerBoy said:**
> I edited my previous post with link to MythTV soln no alsa asound fiddling required.

The asound alsa stuff just/can screws up pulse & other apps.

If you use a custom alsa mixer then S/PDIF digital pass thru' (AC3 DTS) will not work.

If you use internal volume control (mythTV) digital pass thru' will fail.

Thank you for the info.

At the end of the post you link to he says.

{As you explained, when it is playing 2 ch it will be passed to HDMI, but if
more channels chosen, then it will be passed to passthrough device..
This was not how it was setup last it worked, but it seems its ok now.}

So, any time that tv is broadcasting in dolby digital, it will be passed to the spdif out.  The hdmi will not work.  So I must use my stereo.
That is not what I want.
I want alsa to "fix" it so it will correctly pass the sound (any source)  so my tv can also play it.

Also, I do not use pulse.  I do not use internal volume controls, and I have a custom asound.conf, that does passthrough to both spdif and hdmi.
That is the problem I am trying to correct.
I really appreciate the help.  But this is not a mythtv setup question.
My question is, How do I set up alsa so it will correctly convert any sound on my hdmi output.

hardware

Zotac MAGHD-ND01-U MAG All-In-One MiniPC 

video driver	

nvidia 260.19.29

alsa version
 
1.0.23

aplay -L

kevin@mythbigscreen:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=NVidia
    HDA NVidia, ALC888 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output

asound.conf
pcm.!default {
type plug
slave {
pcm "both"
}
}

pcm.both {
type route
slave {
pcm multi
channels 6
}
ttable.0.0 1.0
ttable.1.1 1.0
ttable.0.2 1.0
ttable.1.3 1.0
ttable.0.4 1.0
ttable.1.5 1.0
}

pcm.multi {
type multi
slaves.a {
pcm "tv"
channels 2
}
slaves.b {
pcm "receiver"
channels 2
}
slaves.c {
pcm "analog"
channels 2
}
bindings.0.slave a
bindings.0.channel 0
bindings.1.slave a
bindings.1.channel 1
bindings.2.slave b
bindings.2.channel 0
bindings.3.slave b
bindings.3.channel 1
bindings.4.slave c
bindings.4.channel 0
bindings.5.slave c
bindings.5.channel 1
}

pcm.tv {
type hw
card 0
device 3
channels 2
}

pcm.receiver {
type hw
card 0
device 1
channels 2
}

pcm.analog {
type hw
card 0
device 0
channels 2
}

---

### Post by BicyclerBoy on 2011-01-14
Thought is was a soln sorry.
You can pick the stereo 2ch PCM track from menu for TV or amp.
Pick the AC3/DTS for HT amp.
All DVDs must have 2 ch PCM & I think the same applies to dvb.

Do you really mean digital pass thru' or just 2ch stereo PCM S/PDIF & LPCM HDMI.
Digital pass thru' is not so trivial to achieve.
HT amps AVRs can be very picky with any changes to the datastream of AC3/DTS.

From what I have read, digital pass thru' can not be achieved with internal volume, mixer, equaliser up or down mixing.
I did not think you can digital pass thru' to two outputs simultaneously but this seems an odd limitation now with multiple digital outputs.. 

AFAIK MythTV is the only place you will be able to control digital pass thru'.

I believe you can recode the audio into AC3 with pulse audio

---

### Post by iitywygms on 2011-01-14
Well, after reading further from different sources, I have come to the conclusion that this is just not possible at the moment.  I can have alsa resample the audio and output it to both the hdmi and spdif out.  Or, I can have alsa do passthrough on both the hdmi and spdif.  But I cannot have alsa output one passthrough, and the other one resampled.  Just not possible at this time.
I have read that pulse audio may be able to do this.
Oh well, thank you for all the suggestions.
Hopefully someday it will be possible.

---

### Post by BicyclerBoy on 2011-01-14
I think you can still send LPCM over HDMI & digital pass thru' to S/PDIF (pulse audio).

LPCM supports multi-channel HD audio so is superior to S/PDIF in all ways.
The sound quality out of any TV is terrible anyway so send anything to it !

AC3 DD5.1 & DTS are inferior to LPCM & HD audio formats.

Can you use the S/PDIF pass thru' output on the TV, some allow AC3/DTS out (matrix 5.1) as well 2ch stereo PCM. 
i.e. HTPC --> TV --> AVR

(Need TV on to listen to music..)

Pulse audio is not meant to be a bad thing.

---

