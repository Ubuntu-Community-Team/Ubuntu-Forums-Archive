---
title: "Help with HDMI Surround Sound (5.1)"
date: 2011-01-10
forum: Mythbuntu
---

### Post by the_pod on 2011-01-10
Hi.  I'm looking for a little help in trying to get my Myth setup to output 5.1 via HDMI.  This may be simple (and may already be happening), but I'm a bit stumped.

As info, using .23 in Mythbuntu 10.04.  I have an ATI 3200 onboard card w/ embedded HDMI output.  Onboard sound card is disabled.  Am using the non-ATI drivers since these were causing my video/audio to stutter w/ ALSA.

aplay -l results in:
```
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

aplay -L results in:
```

null
    Discard all samples (playback) or generate zero samples (capture)
hdmi:CARD=HDMI
    HDA ATI HDMI, ATI HDMI
    HDMI Audio Output
```

I just got a new receiver that takes an HDMI in, so that is receiving the HDMI and resulting TV picture (not sound) is being pushed to TV via HDMI as well.

Question - Am I currently running in 5.1?  I don't think I am if I'm reading the receiver manual properly.

I am currently running ALSA and not PulseAudio.  Further confounding the situation, is that if I install PulseAudio, it only gives me an option to output in Stereo. It seems to me that Surround Sound (5.1) should be an option.

Thanks for any help. We just had a baby this weekend so I've got little else to do but surf the board and try to get this working right (finally).

---

### Post by nickrout on 2011-01-11
In mythtv frontend go to setup|general and about page 3 or 4 is audio settings.

scan for audio devices and then you can left and right arrow through the detected devices, and down the bottom will be alist of capabilities for each device. The one you want is **probably** Alsa:hdmi, but see whats there.

Also you need a 5.1 source to get 5.1  to the receiver. Is your source material 5.1? You can also get myth to upmix a stereo source to 5.1, although it won't be true 5.1, just a mix of the stereo channels to fill all the speakers.

Also if your source has ac3 sound or dts sound, you need to click the boxes to pass through those streams.

---

