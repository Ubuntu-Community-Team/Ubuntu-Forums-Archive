---
title: "sound issues"
date: 2006-12-20
forum: Multimedia &amp; Video
---

### Post by striketh on 2006-12-20
For some odd reason, sound is not working in any videos. MP3's play fine in xmms, however no matter what I try I can't get any videos to play sound (using alsa) I'm using the Audigy2 card. None of the video players spit out any errors either..it plays fine, just without sound. Both MPlayer and VLC have this issue. I ran "sudo ln -s /tmp/.esd-1000 /tmp/.esd" before as it was posted somewhere as a solution but I think it only made things worse. Any help would be appreciated.

$ aplay -l **** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 Value [SB0400]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Audigy2 [Audigy 2 Value [SB0400]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 Value [SB0400]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M5455 [ALi M5455], device 0: Intel ICH [ALi M5455]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M5455 [ALi M5455], device 2: Intel ICH - IEC958 [ALi M5455 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

