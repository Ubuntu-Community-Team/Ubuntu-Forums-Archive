---
title: "All audio output is very choppy"
date: 2011-10-31
forum: Multimedia Software
---

### Post by dasy2k1 on 2011-10-31
All playback audio is very choppy since upgrading from 11.04 to 11.10
with a lot of squelching noises.

I used to get this problem from time to time on 11.04 but restating the x server usially fixed it.


running on 5.1 speakers with hardware set to analouge 5.1 output and analouge sterio input
```

dasy2k1@dan-ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dasy2k1@dan-ubuntu:~$ 


```

---

### Post by dasy2k1 on 2011-11-02
Just noticed that when i try to change the hardware setup in sound settings to analogue 5.1 output with analogue stereo input it changes straight back to analogue stereo duplex...

it also keeps jumping between the analogue output and analogue headphones connector setting

when a jack is loaded into the front headphone socket everything seems to work as it should. (as soon as you remove it it breaks again)

i have the following modules loaded in the kernel with repect to sound 

```
dasy2k1@dan-ubuntu:~$ lsmod | grep snd
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
dasy2k1@dan-ubuntu:~$ 

```

---

