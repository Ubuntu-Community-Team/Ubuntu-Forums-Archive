---
title: "M-audio 24/96, no sound in flash.."
date: 2011-02-07
forum: Multimedia Software
---

### Post by Daliz on 2011-02-07
I'm using Kubuntu 10.04 LTS (no pulseaudio).

I'm having some troubles with my soundcards. I have a Audigy ES PCI soundcard and I just recently bought an M-Audio Audiophile 24/96 soundcard and at the moment I have both of them installed. I'm dual booting w/ Windows xp and I need the Audigy in Windows for gaming and because of the mic input that the M-Audio doesn't have.

First when I installed the M-Audio only Amarok (and probably other 'Phonon' apps) worked but I had no sound in mplayer, xine etc. With some googling I found a way to make the M-Audio card the primary card for Alsa and now mplayer & xine work fine too. M-audio 24/96 uses the module ice1712.

Today I noticed I don't have sound in flash player (I use opera, but tried firefox too), and the (alsa?) command aplay won't play any .wavs. Flash sounds used to work okay with only the Audigy installed. I have tried to reinstall the flash player.

Aplay -l :
```

**** List of PLAYBACK Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy [SB Audigy 1 ES [SB0160]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Audigy [SB Audigy 1 ES [SB0160]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8                                                                                                                                                                  
  Subdevice #0: subdevice #0                                                                                                                                                       
  Subdevice #1: subdevice #1                                                                                                                                                       
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy [SB Audigy 1 ES [SB0160]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Googling around I found a command to use with aplay:
aplay -D plughw:0,0 /usr/share/sounds/alsa/Front_Center.wav

The .wav plays just like it should.. only I don't know what's the difference between 'hw' and 'plughw'. Aplay doesn't play any sounds without specifying the 'plughw' thing.

Also, Wine doesn't seem to like the M-audio card so if there's a way to make Wine use the Audigy that would be great. Or if Wine can be configured to use the M-audio card. I use Spotify free through Wine.

Any ideas, please post.

Thanks


Edit: It seems that mplayer only works when OSS is selected, same with Avidemux. Xine, VLC and Audacity work ok with ALSA default settings. Still no sound in flash.

---

### Post by Daliz on 2011-02-09
Solution: Remove ALSA, install OSS4, everything works, no extra configuring needed. :popcorn:

---

