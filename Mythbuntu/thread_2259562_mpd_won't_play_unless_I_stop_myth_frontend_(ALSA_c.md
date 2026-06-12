---
title: "mpd won't play unless I stop myth frontend (ALSA conflict)"
date: 2015-01-05
forum: Mythbuntu
---

### Post by kpatz on 2015-01-05
I recently upgraded my Mythbuntu system from 10.04 to 14.04.  I did a fresh install and then restored the Myth database and reconfigured everything.

I use the onboard sound (SPDIF output) for MythTV.  This works fine.  I also have a separate sound card that connects to my whole house audio system to play music using mpd.

Ever since I upgraded, mpd won't play unless I stop mythfrontend, then restart mpd.  Once mpd starts playing successfully I can restart mythfrontend and everything works fine.

This is the error I get in mpd.log:

```

Jan 04 19:44 : alsa_output: Failed to open "Whole House" [alsa]: Failed to open ALSA device "hw:CARD=CMI8738,DEV=0": Device or resource busy

```

This is what I have in the audio_output section of mpd.conf:
```

audio_output {
        type            "alsa"
        name            "Whole House"
        device          "hw:CARD=CMI8738,DEV=0"
#       device          "hw:2,0"        # optional
        format          "44100:16:2"    # optional
#       mixer_type      "software"
        mixer_device    "default"       # optional
        mixer_control   "PCM"           # optional
        mixer_index     "0"             # optional
}

```

Here's the output of aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Card 0 subdevice 1 is the onboard sound which I use for MythTV.  Card 2 subdevice 0 is the sound card that mpd uses.

Audio output device in mythfrontend is **ALSA:iec958:CARD=SB,DEV=0**

So, the issue is, when mythfrontend is running, it doesn't allow mpd to access the 2nd sound card.

Anyone have a solution?  I've tried the various fixes I've found on the interwebs, such as mixer_type "software" in mpd.conf but nothing helped.

I never had this problem in 10.04.  When I looked at my old mythconverg database dump, it looks like I used **ALSA:default** as my output device in the frontend.  Maybe it's something to do with this?

I tried the /etc/asound.conf from the old install on the new.  That didn't help either:

```

pcm.!default {
        type hw
        card 0
        device 1
}

```

---

### Post by kpatz on 2015-01-06
Bump... anyone?  Bueller?  I tried ALSA:default in the frontend but I got no sound, and it didn't solve the mpd conflict either.

Since mpd and myth are using separate physical sound cards there shouldn't be any conflict, in theory at least.

Would turning Pulseaudio off help?  I can't think of what else would be different from 10.04 to 14.04.

---

