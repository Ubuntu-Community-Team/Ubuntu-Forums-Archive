---
title: "amidi"
date: 2009-11-30
forum: Multimedia Software
---

### Post by kjkrum on 2009-11-30
Maybe I misunderstand what amidi is supposed to do... but I can't get it to produce any sound.

```
$ amidi -l
Dir Device    Name
IO  hw:0,0    ES1371
IO  hw:1,0    MPU-401 UART MIDI
$ amidi -p hw:0,0 -s sample.syx
$
```

With either device, amidi just pauses for a few seconds and exits.  I know the sample contains music because I was able to convert it to a standard MIDI file with a DOS program called syx2midi.

Is there a way to get amidi to output to timidity or another software synth?  Or any other player that groks sysex dumps?

Edit: Playing a standard MIDI file with aplaymidi produces silence for the expected duration of the music.

---

