---
title: "Can't synthonize all channels"
date: 2010-11-13
forum: Multimedia Software
---

### Post by sanflores on 2010-11-13
I have a Pinnacle 110i that works great, exelent sound (I used a cable in from sound out from the tv card to line in in the sound card)
but I can not synthonize all channels, for example, I can't see 7,24,25,26,27,28,29,30,42,43,44...

I use TvTime and when I activate auto deteccion for the channel, it show a blue screen with no-signal message. And when I desactivate auto deteccion, I can hear what is happening in the channel, but the screen is all black

The modul load as default and I haven't had to edit anything in order to make it work.

I've tryied to load the module manually, with exactly the same result
sudo rmmod saa7134_alsa;sudo rmmod saa7134;sudo modprobe saa7134 card=77 pinnacle_remote=1 tuner=54

Here are the options for my county (Argentina)
<option name="Frequencies" value="us-cable"/>
<option name="NTSCCableMode" value="Nominal"/>
<option name="Norm" value="PAL-Nc"/>


Any idea anyone?

I can see with no problem about half the channels, and radio works perfectly

---

### Post by sanflores on 2010-11-18
No one know why is this?

---

