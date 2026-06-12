---
title: "AC3 Audio - Can't hear voices?"
date: 2012-08-30
forum: Multimedia Software
---

### Post by terrykiwi83 on 2012-08-30
Hey all,

I am pretty sure this could be a common problem as I have searched many times through the internet to find a solution but cannot find one that is easy to follow for my Ubuntu 12.04 x64 installation.

Basically I use either VLC or Media Player to play video tracks that have AC3 audio, the background music is prefect. However, the character voices cannot be heard or are sometimes so low it is very tinny (echoed). 

H/W (if needed):

CPU: i7 3770K
MOBO: GA-Z77X-UD3H (I use the on-board sound, plugged in to my 5.1 surround sound system)

So my question is "Does anybody have a fix that will 'sort out' this AC3 issue for good?"

Thanks

---

### Post by BicyclerBoy on 2012-08-31
Assuming you are using 6 discrete analogue outputs to small loudspeakers..
And you have selected 5.1 surround analogue output..

In this case VLC etc decodes the AC3/DTS/etc into 6 discrete channels & soundcard outputs 6 analogue signals.

I would install/run "pavucontrol", this should then give you 6 volume/mixer controls so you can adjust the balance.
Failing that I think VLC has a audio mixer control.
Possibly you have VLC outputting stereo downmix to the surround51 device.
VLC seems to pick the wrong audio track by default.

Could be good idea to run channel order test..
speaker-test -l 2 -c 6 -r 48000 -D surround51

There are a couple of "spoken word" multi-channel audio test tracks on the web in AAC & AC3 formats.

---

