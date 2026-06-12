---
title: "Lossless compressed audio for iPod"
date: 2012-03-12
forum: Multimedia Software
---

### Post by pssturges on 2012-03-12
Hi,

I have a few albums in flac that I would like to be able to play on my iPod/iPhone in a lossless format. Ideally also be compressed somewhat like flac is. Apparently I should be able to use aiff or apple lossless which I know very little about and am not having a whole lot of luck researching. There's even less info about when it comes to doing the conversion in Ubuntu. 

Apparently there are compressed and non-compressed versions of aiff?

My first thought is ffmpeg, but I wouldn't know where to start. 
So, what other tools are there, and how doing I go about achieving compressed,  lossless audio?

Thanks in advance
Phil

---

### Post by ron999 on 2012-03-12
> **pssturges said:**
> 

My first thought is ffmpeg, but I wouldn't know where to start. 

Hi
With FFmpeg, run this command:-
```
ffmpeg -codecs
```
See if alac is on the list.
Like this:-
```
DEA D  alac            ALAC (Apple Lossless Audio Codec)
```

---

### Post by pssturges on 2012-03-12
Yep
```
DEA    alac            ALAC (Apple Lossless Audio Codec)
```
 Don't have the second "D". Does that matter?
Thanks
Phil

---

### Post by ron999 on 2012-03-12
> **pssturges said:**
>  Does that matter?


No, I don't think it matters.:)

To convert from flac to alac with FFmpeg.
Use shantiq's methods ---> [http://ubuntuforums.org/showpost.php?p=11737536&postcount=24]("http://ubuntuforums.org/showpost.php?p=11737536&postcount=24")
Then maybe make a pre-set for WinFF ---> [http://code.google.com/p/winff/wiki/HowToMakePresets]("http://code.google.com/p/winff/wiki/HowToMakePresets")

---

### Post by pssturges on 2012-03-12
Well wasn't tha easy in the end.

Thankyou very much!

---

