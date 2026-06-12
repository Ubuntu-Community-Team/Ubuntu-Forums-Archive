---
title: "MythTv audio output over HDMI"
date: 2010-01-10
forum: Mythbuntu
---

### Post by grogling on 2010-01-10
I am having trouble getting audio to output over HDMI from MythTV.

This is on a Zotac ION mini-ITX motherboard. I am running MythBuntu 9.10 using the MythBuntu supplied Nvidia binary driver.

To begin with, audio wasn't working at all, but after fiddling with unmuting and adding the following to /etc/asound.conf, audio started working in VLC.
> pcm.!default {
        type hw
        card 0
        device 3
}
ctl.!default {
        type hw
        card 0
}


But no matter what I do, MythTV stays silent. I have tried changing the "Audio output device" to many different settings with no luck (I found somehwere VLC is using ALSA, so just put mythtv back to ALSA:Default) and tried fiddling with the passthrough settings, but with no luck.

An interesting thing i have found is in LiveTV, if i press ] to increase volume, it reports volume at 0% but it simply does not move if i press up or down. Does this sound like the problem or is it just a red herring?

I have been presuming that everything outside mythtv should be left as is since VLC is working, but i'm just not sure. I really need help on this one.

Regards

Glen

---

### Post by obryantr on 2010-01-11
Same problem here:
zotac ion a-u
nvdia 185
mythtv 0.22
karmic koala

sound works on VLC both stereo and AC3 passthrough

followed instructions at [http://www.mythtv.org/wiki/AllensDigitalAudioHowto](http://www.mythtv.org/wiki/AllensDigitalAudioHowto) 

unmuted alsa mixer

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

still does not work. On anther note XBMC plays the aac track of movies fine but it won't play the AC3 passthrough either.

funny that it plays all other sounds though?
:(

---

### Post by obryantr on 2010-01-11
OK. Since I had sound in other apps I figured it must  be a problem with a setting in mythtv. So I went back into the frontend utilities/setup>setup>general>audio and tried various combinations. This is what worked!!

Audio output device: ALSA:hdmi
Passthrough output device: Alsa:hdmi
Max Audion Channels: 5.1 (both stereo and 5.1 work)
Upmix: Passive

enable ac3 to spdif passthrough checked
DTS and aggressive buffering all unchecked.

I now have sound WOOOO HOOOO!

---

### Post by zane131 on 2010-01-29
Thanks, this solved my problem. However, now I have a new one. Every time I change the channel on Live TV, I get a short, but loud, cracking sound.

---

### Post by zane131 on 2010-02-01
I fixed the cracking sound by disabling ac3 to spdif passthrough.

---

