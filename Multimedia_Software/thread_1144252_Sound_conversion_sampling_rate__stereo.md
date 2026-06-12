---
title: "Sound conversion sampling rate / stereo"
date: 2009-04-30
forum: Multimedia Software
---

### Post by WitchCraft on 2009-04-30
I need to get my audio file in the correct format to play it in OpenArena.

So far, the first example I tried worked:
```

~/Desktop/openarena-0.8.1/baseoa/music# file working.ogg 
working.ogg: Ogg data, Vorbis audio, mono, 12000 Hz, ~29000 bps, created by: Xiph.Org libVorbis I

```


But the second example didn't work:
```

~/Desktop/openarena-0.8.1/baseoa/music# file notworking.ogg 
notworking.ogg: Ogg data, Vorbis audio, stereo, 44100 Hz, ~112000 bps, created by: Xiph.Org libVorbis I

```

Most important:
How can I adjust mono/stereo and the frequency etc. ?

Secondary question:
Anybody knows what's the exact requirements to ogg file settings for OpenArena ?

---

### Post by WitchCraft on 2009-04-30
> **WitchCraft said:**
> 
Most important:
How can I adjust mono/stereo and the frequency etc. ?

Secondary question:
Anybody knows what's the exact requirements to ogg file settings for OpenArena ?

Oh got the answer myself:

Conversion with: 
```

apt-get install soundKonverter

```

Exact requirements:
- Frequency: <=32000 Hz
- Channels:  mono only !!!

---

