---
title: "Convert to FLAC"
date: 2009-02-20
forum: Multimedia Software
---

### Post by DPic on 2009-02-20
So, i need to convert some mp3's to FLAC files. I know this is not a good idea (generally for being a waste of space and having the same quality of the lossy mp3) but i want to upload an album to Jamendo and i only have an mp3 copy. 

I have tried Sound Converter and tried converting it to FLAC and WAV but Jamendo rejected the files both times. When i tried the desktop uploader, it gave an error saying it required 16 bit depth so i think that might be the problem. If i look at the auto properties through nautilus is says the bit rate is n/a but i'm not sure if that is the same thing. 

Can anyone help me fix this?

---

### Post by andrew.46 on 2009-02-21
Hi,

Well there are a few ways I guess. A suitably configured FFmpeg will do it for you:

```
$ ffmpeg -i infile.mp3 outfile.flac
```

also a suitably configured SoX will do the same:

```
$ sox -S infile.mp3 outfile.flac
```

And you could do it the long way with MPlayer and flac:

```
$ mplayer infile.mp3 -ao pcm:fast:waveheader:file=outfile.wav
$ flac --best outfile.wav -o final.flac
```

All depends on your available software and taste :-). In the little bit of experimentation I did with this I found that the SoX conversion sounded the best.

Andrew

---

