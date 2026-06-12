---
title: "nVidia MCP51 High Definition Audio not working after upgrade"
date: 2008-04-28
forum: Multimedia Software
---

### Post by SagaciousKJB on 2008-04-28
Hello everyone, I'm having some problems with my graphics and audio controllers after an upgrade from Gutsy Gibbon to Hardy Heron.  I've sorted out the video problems, but after following the Comprehensive Sound Problems Guide without any success, I'm not unconvinced that the upgrade did not go so well.

The device is recognized in lspci, the modules show up in lsmod, and alsa shows it as a perfectly working card, however sound simply does not work.  I even went so far as to check the auxilary cords plugged into the speaker didn't fall out after years of being in the same secluded, hard-to-get-to spot, and they were in place.  Something I probably could have determined when I got that terrific buzz when I unplugged and plugged the cord back into my soundcard.

The card requires the hda-intel module ( snd-hda-intel in ubuntu ) according to this page: [http://hardware4linux.info/component/16077/](http://hardware4linux.info/component/16077/)  I'm quite sure this is correct, because I also recall having to load this module manually when I upgraded from 6.10 to 7.04 too.  The only difference is it actually worked that time.

I tried the ALSA-driver compilation using alsa-source according to the Comprehensive Sound Problems Guide, and got no errors on the compilation process, and no error when I loaded the new module.  However, still no sound.  I'm quite sure that there is no hardware issue and that all of the connections are in place, and nothing seems to be muted in alsamixer either.

lspci -v | grep -i audio
```
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
02:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
```

lsmod | grep snd
```
snd_emu10k1_synth       8064  0
snd_emux_synth         36224  1 snd_emu10k1_synth
snd_seq_virmidi         8192  1 snd_emux_synth
snd_seq_midi_emul       7552  1 snd_emux_synth
snd_emu10k1           146880  4 snd_emu10k1_synth
snd_ac97_codec        101028  1 snd_emu10k1
ac97_bus                3072  1 snd_ac97_codec
snd_util_mem            5632  2 snd_emux_synth,snd_emu10k1
snd_hda_intel         344728  1
snd_hwdep              10500  3 snd_emux_synth,snd_emu10k1,snd_hda_intel
snd_pcm_oss            42144  0
snd_pcm                78596  5 snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  3 snd_emu10k1,snd_hda_intel,snd_pcm
snd_mixer_oss          17920  1 snd_pcm_oss
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8320  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                54224  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9612  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  22 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [SBLive! Value [CT4780]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 1: Live [SBLive! Value [CT4780]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Live [SBLive! Value [CT4780]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Everything seems to be in working order, but it still fails to actually produce any sound.  It is also obviously not a problem with ALSA or any other lower-level sound issue, as my second SBLive! card is working perfectly.  I'm not sure if there is something exceedingly simple I've missed, or if something in the upgrade process went awry.  I used the Version Upgrade tool in the Adept manager, if that makes it any easier to determine what might have happened.

---

