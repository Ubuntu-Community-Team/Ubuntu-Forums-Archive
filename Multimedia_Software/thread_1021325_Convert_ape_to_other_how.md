---
title: "Convert ape to other: how?"
date: 2008-12-25
forum: Multimedia Software
---

### Post by johann_p on 2008-12-25
Is there some recommended way to convert a single .ape file to individual mp3s easily?                                          

I have tried without any success to convert and split a file in .ape+.cue format to some other format. Practically all the instructions I found in these forums or elsewhere on the web rely on something that does not exist anymore, is broken, or simply does not work.

My only success was with [FONT=monospace]
[/FONT]```
ffmpeg -i inputaudio.ape outputaudio.flac
```However when I try to split the resulting .flac file with 
```

shntool split -f filename.cue -o flac filename.flac

```I get the error messages:
```

shntool [split]: warning: discarding initial zero-valued split point
shntool [split]: error: split points go beyond input file's data size

```All the other approaches using audio-convert or similar did not work at all.

So - Is there some recommended way to convert a single .ape file to individual mp3s easily?

---

