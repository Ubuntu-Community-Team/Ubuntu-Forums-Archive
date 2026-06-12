---
title: "ALSA, hardware, missing device"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by agharbeia on 2007-11-24
Greetings,

Sounds works well for me. Except that it hangs some some times when I, for example, work with Audacity while running Totem/GStreamer, as it starts jittering the same note forever.

However, whenever ALSA is stopping, either in shutdown or manually, the following error message is logged a number of times:

<samp>
amixer: Mixer hw:1 load error: Invalid argument
</samp>


When ALSA is starting the following warning is logged:

<samp>
warning: 'alsactl restore' failed with error message 'alsactl: set_control:1159: Cannot write control '2:0:0:Mic Capture Switch:0' : Invalid argument'...
</samp>

and then the previous error is then logged for a number of times. ALSA loads successfully eventually.


Running <kbd>aplay -l</kbd> yields:

<samp>
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SBLive 5.1 [SB0060]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
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
card 0: Live [SBLive 5.1 [SB0060]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SBLive 5.1 [SB0060]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
</samp>


As you can see there's no "device 1" in the enumeration above, which corresponds to the ALSA startup/shutdown message complaining about "hw1"

Also, the subdevices of device 0 are counted as 31/32, but in fact 32 subdevices are enumerated, from 0 to 31!

Other connected devices that have sound capability are a Logitech USB webcam.

This is a fresh Gutsy install. I don't remember having this problem in Feisty.

Any insights about this error message and whether it has anything to do with ALSA hanging from time to time.

Regards,

---

### Post by agharbeia on 2007-12-24
A slight improvement, since [my last post]("http://ubuntuforums.org/showthread.php?t=622019"):
Running <kbd>aplay -l</kbd> now reports the correct number of subdevices under each device. More specifically, "card 0: Live [SBLive 5.1 [SB0060]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]" now has "Subdevices: 31/32"

However, device "1" is still missing, since the next device reported is "card 0: Live [SBLive 5.1 [SB0060]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]", and the "amixer: Mixer hw:1 load error: Invalid argument" still appears whenever ALSA is starting or stopping.

Moreover, I still experience occasional, unexpected hanging of "sound", whereby any playing sound jitters so much and progresses very slowly. This has nothing to do with the CPU utilisation.

---

