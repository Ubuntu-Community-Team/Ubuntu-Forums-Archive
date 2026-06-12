---
title: "Two sound outputs, default sound to one, music to another"
date: 2008-12-06
forum: Multimedia Software
---

### Post by timkoop on 2008-12-06
Hi everyone.  I just got a "new" sound card with two sound out ports.  I would really like to pipe out all default sound to one and my music to another.  This way I can play games and hear the sound on my small computer speakers, and I can listen to my music through my big stereo.

I've read some old how-to's, but I don't know if they still apply to 8.10.

Sound is currently working through one of the ports.  I guess I need to know how to divert just a few application's sound (like Listen Music Player and Totem and maybe Firefox) to the other output.

This is what I have:

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Any advice or commands to run would be appreciated, or any how-to's that are still current would help too.

I'm experienced with Linux, but I know nothing about how sound works.

Thanks a lot!

-- 
Tim

---

### Post by VictorR on 2008-12-06
You can try using PulseAudio to forward audio streams to different outputs. In Intrepid PulseAudio is not completely installed by default, so open Synaptic, search for "pulse" and check if you have padevchooser and paprefs installed as well as other libraries for particular apps you may need.

Then launch Pulse Audio Device Chooser, select Playback tab, run apps you want to re-direct, its stream should appear in PA Device Chooser, and "Move Stream" to the proper output.
PulseAudio should remember this for the next time.

See this [PulseAudio Documentation]("http://www.pulseaudio.org/wiki/Documentation"), if something does not work, as expected.

---

### Post by VictorR on 2008-12-06
You can try using PulseAudio to forward audio streams to different outputs. In Intrepid PulseAudio is not completely installed by default, so open Synaptic, search for "pulse" and check if you have padevchooser and paprefs installed as well as other libraries for particular apps you may need.

Then launch Pulse Audio Device Chooser, select Playback tab, run the app you want to re-direct, its stream should appear in PA Device Chooser, and "Move Stream" to the proper output.
PulseAudio should remember this for the next time.

See this [PulseAudio Documentation]("http://www.pulseaudio.org/wiki/Documentation"), if something does not work, as expected.

---

