---
title: "wav file meta data after ripping audio cd"
date: 2014-09-02
forum: Multimedia Software
---

### Post by greg59 on 2014-09-02
I am not doing very well at ripping an audio cd correctly. Using two different applications (ripperX, k3b), I have succeeded in creating a folder of wav files named with the artist and track names. However when I load this data onto my mp3 player (which supports wav files) it ends up in its unknown folder along with everything else I have in there (so it is awkward to play them in sequence) 

Right clicking any of these files, choosing properties and looking at the Audio tab I am presented with the following data in roughly this format:

**General**:

  Title:        Unknown
  Artist:      Unknown
  Album:     Unknown
  Year:        Unknown
  Duration:   3 minutes 42 seconds
[B]
Audio:[/B]

  Codec:           Uncompressed 16-bit PCM audio
  Channels:       Sterio
  Sample Rate:  44100 Hz
  Bitrate:           N/A


I imagine there needs to be some data embedded into these files in order to populate the fields above, but I don't know what I am doing yet. Further I imagine there is either some gui or command line tool that can do this job for me but for all my google searching and messing about (3 hours so far) I have come up with nothing. 
Further if I knew what would be the expected format of this data assuming it isn't in the same unprintable chars as most of the rest of the file) I would be tempted to open them up with vim (in binary mode) and hack in the data directly.

Any ideas?


Edit .. after reading some of the posts here it was suggested to use "Sound Converter" tried this though it still didn't allow me to directly add any tag data - but then it also pointed me towards sound juicer which seems to be adding the meta data I require ...

Ok ... I think the solution to this one is beyond the scope of this thread ... even with the meta data it still can't be catelogued on my player (still gets thrown into Unknown) :/

Final edit: 7th rip is a charm - on sound juicer choose sortable naming type (not the default)

---

### Post by FakeOutdoorsman on 2014-09-03
Metadata in WAV is going to be hit-and-miss in terms of what can write and what can read it. As for as I know there is no official standard for putting metadata in WAV, but some tools like Audacity use RIFF LIST INFO tags and ID3 tags: [http://wiki.audacityteam.org/wiki/WAV#Metadata](http://wiki.audacityteam.org/wiki/WAV#Metadata)

---

