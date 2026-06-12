---
title: "Java MidiUnavailableException"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by virogenesis1 on 2007-11-10
Hi, I am getting the above error when trying to access javax.sound.midi.MidiSystem. I am trying to run the program MiniMiniMusicApp which uses this java class to get the system default MIDI sequencer. I am running 7.10, and have checked that my soundcard has a MIDI port:

```
aplaymidi -l
 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
128:0    TiMidity                         TiMidity port 0
128:1    TiMidity                         TiMidity port 1
128:2    TiMidity                         TiMidity port 2
128:3    TiMidity                         TiMidity port 3

```

have also tried:

```
 lsmod | grep snd_seq
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  12 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

```

and the program compiles fine. But when I run it I get the following stacktrace:
```

 java MiniMiniMusicApp 
javax.sound.midi.MidiUnavailableException
        at javax.sound.midi.MidiSystem.getDefaultDeviceWrapper(MidiSystem.java:1096)
        at javax.sound.midi.MidiSystem.getReceiver(MidiSystem.java:258)
        at javax.sound.midi.MidiSystem.getSequencer(MidiSystem.java:460)
        at javax.sound.midi.MidiSystem.getSequencer(MidiSystem.java:366)
        at MiniMiniMusicApp.play(MiniMiniMusicApp.java:14)
        at MiniMiniMusicApp.main(MiniMiniMusicApp.java:7)
Caused by: java.lang.IllegalArgumentException: Requested device not installed
        at javax.sound.midi.MidiSystem.getDefaultDevice(MidiSystem.java:1148)
        at javax.sound.midi.MidiSystem.getDefaultDeviceWrapper(MidiSystem.java:1094)
        ... 5 more

```
:confused:

Google has been unhelpful, I haven't been able to find anything specific on the Sun forums, so I wonder if anyone here has any pointers?

Thanks in advance

---

