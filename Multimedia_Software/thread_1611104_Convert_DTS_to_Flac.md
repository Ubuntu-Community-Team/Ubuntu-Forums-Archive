---
title: "Convert DTS to Flac"
date: 2010-11-01
forum: Multimedia Software
---

### Post by wieman01 on 2010-11-01
Hi, 

How can I convert DTS files to Flac? Soundconverter and the likes won't work, so I thought of VLC but could not get it to work either.

Any foolproof solution out there?

---

### Post by ron999 on 2010-11-01
Hi
Have you tried using ffmpeg?
Like this:-
```
ffmpeg -i filename.dts filename.flac
```

---

### Post by xc3RnbFO8P on 2010-11-01
**SoundConverter**
and libdca0

---

### Post by wieman01 on 2010-11-02
> **ron999 said:**
> Hi
Have you tried using ffmpeg?
Like this:-
```
ffmpeg -i filename.dts filename.flac
```
Tried this, but I only hear noise when I replay the resulting Flac file.

---

### Post by wieman01 on 2010-11-02
> **Ringi said:**
> **SoundConverter**
and libdca0
Tried this too, but same problem as above... I only hear noise afterwards.

---

### Post by xc3RnbFO8P on 2010-11-02
> **wieman01 said:**
> Tried this too, but same problem as above... I only hear noise afterwards.

I converted this [file]("http://www.diatonis.com/downloads/diatonis_dts_wav_secret-universe.zip") and it came out fine.

---

### Post by wieman01 on 2010-11-02
Ringi, 

I will try again... But please remove that file, it could create a legality issue.

---

### Post by xc3RnbFO8P on 2010-11-02
> diatonis - The Secret Universe 
Free DTS Download 44.1kHz Sample Rate (60 MB)
Its free :)

Are you sure that you all the codecs installed (gstreamer)

---

### Post by wieman01 on 2010-11-02
> **Ringi said:**
> Its free :)

Are you sure that you all the codecs installed (gstreamer)
Ah... :-)

Which 'gstreamer' package would I have to install? Just installed 'gstreamer-tools' but it does not seem to be the right one.

Thanks for your help by the way! :-)

---

### Post by cascade9 on 2010-11-02
DTS to flac? *blinks* DTS is lossy (apart from DTS-HD Master audio), so its probably better to just keep the .dts fles, as lossy-> lossless transcode wont be lossless. It will just make huge files compared to the original. 

If you have to transcode for some reason then .ogg vorbis would be better IMO.

---

### Post by wieman01 on 2010-11-02
> **cascade9 said:**
> DTS to flac? *blinks* DTS is lossy (apart from DTS-HD Master audio), so its probably better to just keep the .dts fles, as lossy-> lossless transcode wont be lossless. It will just make huge files compared to the original. 

If you have to transcode for some reason then .ogg vorbis would be better IMO.
Didn't know it was lossy... OK, then let's drop the whole issue. 

I was just curious if it is possible. Thanks for your help, guys!

---

### Post by xc3RnbFO8P on 2010-11-02
Here is what I got installed in Synaptic...

> It will just make huge files compared to the original.
60 mb .dts > 58 mb .flac

---

### Post by cascade9 on 2010-11-02
> **wieman01 said:**
> Didn't know it was lossy... OK, then let's drop the whole issue. 

I was just curious if it is possible. Thanks for your help, guys!

LOL, sorry to ruin things. 

BTW, I have done dts-> flac (5.1) transodes, 'just to see if can be done'. I used foobar2000, and IIRC I got 3000k/sec flac. Huge files.....

---

### Post by wieman01 on 2010-11-02
> **Ringi said:**
> Here is what I got installed in Synaptic...
Yes, I got those too... Weird, but anyway let's close this thread. I now know it's possible, that's good enough.

Thanks for your help, my friend! :-)

---

