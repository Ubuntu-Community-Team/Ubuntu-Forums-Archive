---
title: "Really annoying sound problem!"
date: 2010-02-27
forum: Multimedia Software
---

### Post by #r00t on 2010-02-27
Hey everyone!

Ok, I've been working on getting Ubuntu 9.10 up and running all through the night, and so far I've gotten everything perfect, except for 1 thing...

When I play audio, with ANY player, in ANY format (MP3, OGG, Video File, Etc.), there is a ~5 second lag from when the audio starts to play, until the sound is actually produced.

I have un-installed and re-installed more codecs and whatnot than I can remember, I have tried a half a dozen media players, and another half a dozen different media formats.

But no matter what I am playing, and what I am playing it with, I can start a song/video, and it will play for anywhere from 3-9 seconds before the sound 'kicks in'.

This is both with my built-in laptop speakers, as well as with the headphone jack.

The laptop is a Toshiba Satellite X205-S7483

The sound card is a Realtek ALC268 with an Intel 82801HBM ICH8M High Definition Audio Controller

aplay -L spits out the followiing:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

My alsa-base file is empty... And when checking 'sudo alsamixer' everything appears to be just fine, and un-muted...

I just can't for the life of me figure out why there is a lag in the sound!

Fwiw, the sound has always worked fine, including with Windows Vista, Windows 7, And Ubunty 8.04 and 8.10 in the past (albeit the sound was a pain to get working at all on old Ubuntu releases, I did manage it 2 separate times).

I got my built-in speakers working (both the 2 tweeters, as well as the 2 mini-subwoofers), as well as my headphone jack, and even my HDMI audio/video, but for some reason, I can't figure out the audio lag.

Any help would be greatly appreciated!! 

Thanks in advance!

---

