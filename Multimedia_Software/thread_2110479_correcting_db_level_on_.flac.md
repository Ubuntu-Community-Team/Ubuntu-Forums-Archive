---
title: "correcting db level on .flac"
date: 2013-01-30
forum: Multimedia Software
---

### Post by mike acker on 2013-01-30
has anyone found a good program for correcting music tracks to 0db ?

the program should scan each track to determine the peak level encountered and then asdjust the entire track so that the peak is at 0db

---

### Post by SeijiSensei on 2013-01-30
Have you tried [Audacity]("https://help.ubuntu.com/community/Audacity")?  I've only used a couple of its filters, mostly for noise reduction, but it seems to offer a lot of control over audio streams.  I know its noise-reduction filter is based on sampling.

---

### Post by evilsoup on 2013-01-30
It's not a one-step thing, but with ffmpeg you can use the volumedetect audio filter to find out the level of the audio:

```

ffmpeg -y -i input.flac -filter:a 'volumedetect' -f wav /dev/null

```It will spit out stuff like this:

> 
[Parsed_volumedetect_0 @ 0x9890820] mean_volume: -27.5 dB
**[Parsed_volumedetect_0 @ 0x9890820] max_volume: -3.3 dB**
[Parsed_volumedetect_0 @ 0x9890820] histogram_3db: 10
[Parsed_volumedetect_0 @ 0x9890820] histogram_4db: 31
[Parsed_volumedetect_0 @ 0x9890820] histogram_5db: 43
[Parsed_volumedetect_0 @ 0x9890820] histogram_6db: 196
[Parsed_volumedetect_0 @ 0x9890820] histogram_7db: 199
[Parsed_volumedetect_0 @ 0x9890820] histogram_8db: 268
[Parsed_volumedetect_0 @ 0x9890820] histogram_9db: 517
[Parsed_volumedetect_0 @ 0x9890820] histogram_10db: 939
[Parsed_volumedetect_0 @ 0x9890820] histogram_11db: 1532


For your purposes, the bolded line is what you should pay attention to, since that is the peak. In this case, to raise the audio so that the peak is 0dB, you would use the volume audio filter.

```

ffmpeg -i input.flac -filter:a 'volume=3.3dB' -c:a flac output.flac

```

If you wanted to reduce the volume, you could use 'volume=-3.3dB' or something similar.

I'm sure there are other tools that can do this better, like sox.

---

### Post by mike acker on 2013-01-30
> **SeijiSensei said:**
> Have you tried [Audacity]("https://help.ubuntu.com/community/Audacity")?  I've only used a couple of its filters, mostly for noise reduction, but it seems to offer a lot of control over audio streams.  I know its noise-reduction filter is based on sampling.

  yep, Audacity is a really great program but I need something that can be applied into a sub-directory rather than 1 track at a time

---

### Post by mike acker on 2013-01-30
> **evilsoup said:**
> It's not a one-step thing, but with ffmpeg you can use the volumedetect audio filter to find out the level of the audio:

```

ffmpeg -y -i input.flac -filter:a 'volumedetect' -f wav /dev/null

```It will spit out stuff like this:



For your purposes, the bolded line is what you should pay attention to, since that is the peak. In this case, to raise the audio so that the peak is 0dB, you would use the volume audio filter.

```

ffmpeg -i input.flac -filter:a 'volume=3.3dB' -c:a flac output.flac

```If you wanted to reduce the volume, you could use 'volume=-3.3dB' or something similar.

I'm sure there are other tools that can do this better, like sox.

ok i got the pdf for sox
ill try working with that it appears to be able to do most anything

---

