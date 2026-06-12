---
title: "ffmpeg time bug"
date: 2010-08-16
forum: Multimedia Software
---

### Post by lucasart on 2010-08-16
I downloaded some *.wma files, and unfortunately my Ipod doesn't play wma files (obviously apple do it on purpose to impose their format over microsoft's).

So I went ahead and converted all of them to MP3, using variable bitrate and a reasonably good quality, by means of

```

ffmpeg -i foo.wma -acodec libmp3lame -aq 4 foo.mp3

```everything works fine, except the time of the songs according to rhythmbox, my ipod, even nautilus under file properties is wrong and vastly overstated. Also the bitrate as it is displayed is wrong (it says 32 kbps when i know it's more around 130-150 kbps).

It's not a big deal as the files play, but it's just silly because the progress bar doesn't allow me to move in the song because of that bug (I often exceed the boundaries of the song). I just don't understand what I did wrong. Are the time and bitrates tags that i should edit with id3v2 ? Or is it just a stupid bug in ffmpeg ot in libmp3lame ?

PS:
* I use Ubuntu 10.04 32 bit, and both ffmpeg and libmp3lame are up to date as in the Ubuntu/Medibuntu repositries.
* I have found a solution to my problem which is to ffmpeg into wma and pipe that into neroAacEnc, to produce an MPEG 4 contained HEv2-AAC. But, even though this encoder is arguably better than mp3, I dont really like using Apple specific crap. If I am forced to use a proprietary format, I might as well choose mp3 which is the most compatible one.

---

### Post by ron999 on 2010-08-16
Hi
I think that you confused ffmpeg by using **vbr**.
That's why it's giving false information about bitrate and time.
Try converting a track using cbr and see if it cures the fault.

(By the way, if I want to use aac on my second generation shuffle, I have to use neroAacEnc.
Apple will only guarantee to play aac files on this model that have been encoded by iTunes.
The faac encoder won't work, but neroAacEnc does.)
:D

---

### Post by FakeOutdoorsman on 2010-08-16
> **lucasart said:**
> ...the progress bar doesn't allow me to move in the song because of that bug...
Progress bar in Rhythmbox or the iPod?

> **lucasart said:**
> ... If I am forced to use a proprietary format, I might as well choose mp3 which is the most compatible one.
Maybe piping directly to LAME will provide better results:
```
ffmpeg -i input.wma -f wav - | lame -V4 - output.mp3
```
I usually use *-aq* instead of *-ab* when encoding music with FFmpeg.  Also, the *-map_meta_data* option sometimes is successful in copying metadata from the input to the output:
```
ffmpeg -i input.wma -map_meta_data 0:0 -acodec libmp3lame -aq 4 output.mp3
```

---

### Post by lucasart on 2010-08-17
> **FakeOutdoorsman said:**
> Progress bar in Rhythmbox or the iPod?


Maybe piping directly to LAME will provide better results:
```
ffmpeg -i input.wma -f wav - | lame -V4 - output.mp3
```I usually use *-aq* instead of *-ab* when encoding music with FFmpeg.  Also, the *-map_meta_data* option sometimes is successful in copying metadata from the input to the output:
```
ffmpeg -i input.wma -map_meta_data 0:0 -acodec libmp3lame -aq 4 output.mp3
```

Thanks!

---

### Post by lucasart on 2010-08-17
> **ron999 said:**
> Hi
I think that you confused ffmpeg by using **vbr**.
That's why it's giving false information about bitrate and time.
Try converting a track using cbr and see if it cures the fault.

(By the way, if I want to use aac on my second generation shuffle, I have to use neroAacEnc.
Apple will only guarantee to play aac files on this model that have been encoded by iTunes.
The faac encoder won't work, but neroAacEnc does.)
:D

MP3 CBR is not very good, VBR is almost as good as Nero AAC HEv2 and OGG and WMA 9 VBR. With the additional advantage for MP3 of compatibility. And faac is a piece of crap: I tested it against MP3 VBR and under 100 kbps I can hear how bad the faac file is whilst the MP3 VBR is indistinguishable to the original. But faac is free software: it's the only reason to use it, if at all. On the other hand OGG is free software and far superior :)

---

### Post by ron999 on 2010-08-17
> **lucasart said:**
> MP3 CBR is not very good, VBR is almost as good as Nero AAC HEv2 and OGG and WMA 9 VBR. With the additional advantage for MP3 of compatibility. And faac is a piece of crap: I tested it against MP3 VBR and under 100 kbps I can hear how bad the faac file is whilst the MP3 VBR is indistinguishable to the original. But faac is free software: it's the only reason to use it, if at all. On the other hand OGG is free software and far superior :)

Very interesting.(NOT) :roll:

---

