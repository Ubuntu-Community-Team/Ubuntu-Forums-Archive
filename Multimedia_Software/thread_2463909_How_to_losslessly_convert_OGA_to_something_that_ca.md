---
title: "How to losslessly convert OGA to something that can be tagged?"
date: 2021-06-21
forum: Multimedia Software
---

### Post by SpectrumDT on 2021-06-21
Hi!

I have a couple of OGA files, extracted losslessly from WEBM files using **ffmpeg**. These have fine audio, but my problem is that I cannot set tags on these OGA files like I can with a normal MP3 or OGG file. 

How can I convert them to a format that allows tags, without loss and without reencoding? Can I somehow wrap them in an OGG or something?

Thanks a lot in advance! :)

---

### Post by TheFu on 2021-06-21
ffmpeg can convert formats easily.

```
$ ffmpeg -i something.oga  -c:a copy output.ogg
```

You could skip the first step by just getting ogg directly instead of the .webm file types. Asking for that should be possible from popular services, using popular tools.

```
$ ffmpeg -i something.webm  **-vn **-c:a copy output.ogg
```

The key is to block video - -vn option does that. Just tested it here. The resulting output.ogg is :
```
$ file output.ogg 
output.ogg: Ogg data, Opus audio,
```

---

### Post by SpectrumDT on 2021-06-22
Thanks a lot! 

What if the WEBM contains Opus rather than OGA audio? Can I losslessly turn this Opus audio file into something that can contain tags (doesn't need to be OGG)?

---

### Post by TheFu on 2021-06-22
Perhaps.  What are the different audio file containers that hold opus encoded audio and your tagging tool can modify the tags inside?  Use that.
This quickly becomes a whack-a-mole problem.  When I've run into it previously, I'd just transcode into the easiest container and audio encoding that worked.  It isn't like flac will be the involved, so the source material will be lossy already.

---

### Post by Yellow Pasque on 2021-06-22
> **SpectrumDT said:**
> What if the WEBM contains Opus?

Then just extract the audio out of the webm file with ffmpeg, and you end up with opus inside ogg container, which can handle metadata/tag easily:
```
ffmpeg -i something.webm something.opus
mediainfo something.opus
```

> These have fine audio, but my problem is that I cannot set tags on these OGA files like I can with a normal MP3 or OGG file

A .oga file should be using an ogg container and should support metadata/tagging. Maybe whatever you are trying to use to tag is getting tripped up by oga extension in the filename. Use mediainfo to see exactly what you're dealing with:
```
mediainfo file.oga
```

---

### Post by TheFu on 2021-06-22
Sometimes ffmpeg will transcode, which the OP is specifically attempting to avoid.  I'm not current on which audio formats a webm container will allow. webm is basically an MKV, just with restrictions on the video and audio encodings allowed.  I'd bet there is a doc somewhere (wikipedia?) which spells out the 3 allowed video and 3 allowed audio codecs.  I don't know that it is 3 for either, but it isn't 50, like mkv handles.

To avoid transcoding, use the -acopy or -c:a copy options in ffmpeg.

---

### Post by Yellow Pasque on 2021-06-22
> **TheFu said:**
> To avoid transcoding, use the -acopy or -c:a copy options in ffmpeg.

I believe that happens automagically if you specify a .opus filename and the source audio is an opus stream.

---

### Post by shantiq on 2021-06-26
> **SpectrumDT said:**
> Hi!

I have a couple of OGA files, extracted losslessly from WEBM files using **ffmpeg**

Would not worry too much about other conversions being a problem; since ogg and oga are already lossy anyway
Personally would simply turn it to an mp3 of exact same bitrate then you do not lose that much
BUT and really this was not lossless in the first instance (i take it you use the work losslessly here as not losing further)
These days audio on DVDs is still almost never lossless most Bluray on the other hand if they are music videos might have really HiRes audio in the 4000kbps range and also maybe 5.1 channel
If the audio on the film you mention here was a rip from a DVD all this is moot really; simply grab the audio to mp3 and then tag if that is your aim here
Anyway that is what i would pick

---

