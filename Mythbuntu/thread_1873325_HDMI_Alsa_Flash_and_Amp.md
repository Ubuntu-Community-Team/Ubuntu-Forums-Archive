---
title: "HDMI Alsa Flash and Amp"
date: 2011-11-01
forum: Mythbuntu
---

### Post by kingmoffa on 2011-11-01
Hi Forum,

I've got a problem on one of my front ends of no sound when trying to play flash movies through mythbrowser. Normal sound through mythtv + mplayer is totally fine. 

The sound did work for a short while through mythbrowser/flash, but then stopped. A reboot of the computer didnt help. 

I have a feeling its because the mythbuntu computer is hooked up via HDMI to an Audio/Video amplifier.  If this is the case, Im hoping that setting a rate in asoundrc file will help. 

Is this valid?

pcm.!default {
type hw
card 2
device 7
rate 48000
channels 6

}

---

### Post by BicyclerBoy on 2011-11-02
Your amp likely supports 22K up to 192KHz, 2 ch to 8 ch.
Why do you think that changing the default alsa alias is going to help ?
I think it will just cause trouble with other output.

The flash audio in browser is very likely using pulse audio.
The pulse audio server most likely does not see the hw:2,7 device.

Can you confirm that pulse audio playback does not output over HDMI ?
Use pavucontrol & check that your default system wide audio device is the correct HDMI device..
If it does not listed then do the following below..(module-alsa-sink).

Undo the !default alias changes in asound.conf/asoundrc file..

Edit file, add at bottom 
/etc/pulse/default.pa:
load-module module-alsa-sink device=hw:2,7
Make sure there is only one module-alsa-sink entry..

Try pulse audio output (rhythmbox etc).

---

