---
title: "Extracting AAC-audio from flv-file and transcoding to mp3"
date: 2008-11-15
forum: Multimedia Software
---

### Post by runesvend on 2008-11-15
Hello

I can't figure out how to get the audio out from an flv-file. Here's what mplayer has to say about the audio:

```
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
```

Using mplayer to dump the audio just produces some data that I can't play with Amarok.

Does anyone know how to get an mp3 file from the audio in this file?

---

### Post by andrew.46 on 2008-11-18
Hi,

Although I am a bigtime MPlayer fan you might be better to use ffmpeg in this case:

```
ffmpeg -i infile.flv -ab 192k -ar 44100 outfile.mp3
```

Compile your own ffmpeg though:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

 All the very best,

  Andrew

---

### Post by runesvend on 2008-11-21
Thanks a lot, that worked perfectly! I initially tried encoding the audio to an mp3 file with mplayer but the command I used just produced garbage, so I got stuck there. Since then I found out that mplayer will output a wave-file without problems, which can then be encoded to mp3 with some other program. This is the command I used:

```
mplayer -ao pcm -vo null -vc dummy infile.flv
```

Both the methods work but your method does it all in one step.

---

### Post by andrew.46 on 2008-11-21
Hi,

Good to hear it all worked out:

> **runesvend said:**
> Thanks a lot, that worked perfectly! I initially tried encoding the audio to an mp3 file with mplayer but the command I used just produced garbage, so I got stuck there. Since then I found out that mplayer will output a wave-file without problems, which can then be encoded to mp3 with some other program. This is the command I used:

```
mplayer -ao pcm -vo null -vc dummy infile.flv
```

Both the methods work but your method does it all in one step.

Mind you I am more used to using MPlayer :-). If you were interested there is a slightly fuller method using MPlayer and the syntx would be:


```
mplayer infile.flv -vc null -vo null -ao pcm:fast:waveheader:file=outfile.wav 
```

which simply makes the encoding marginally faster, allows the possibility of waveheader or not and allows you to specify the output filename. Not totally necessary but it may be useful in other settings.

All the best,

  Andrew

---

