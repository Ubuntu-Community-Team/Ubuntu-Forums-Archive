---
title: "Splitting aac files."
date: 2015-11-09
forum: Multimedia Software
---

### Post by ron998 on 2015-11-09
Hi
To split a long m4a file into half hour sections this command works
```
MP4Box -split 1800 filename.m4a
```
The result is like this
filename_001.m4a
filename_002.m4a
filename_003.m4a
filename_004.m4a
etc.

If the file was aac instead of m4a is it possible to do the job with MP4Box?

If not, is there a **simple** command to use with FFmpeg instead?
So that the result is like this
filename_001.aac
filename_002.aac
filename_003.aac
filename_004.aac
etc.

(I have seen plenty of old threads with convoluted FFmpeg commands, and some scripts :evil:)

---

### Post by andrew.46 on 2015-11-10
I have not tried it (and it will need wine) but the developer of qaac also has an aac cutter:

[https://github.com/nu774/m4acut](https://github.com/nu774/m4acut)

which might be worth a look?

---

### Post by shantiq on 2015-11-10
Hi Ron and Andrew


tested with aac container files from [here]("http://download.wavetlan.com/SVV/Media/HTTP/http-aac.htm") and not happy

each time it says

```
File has 1 tracks
    Track 1 type: Audio (....)
```

and does nothing with MP4Box

===


but at the bottom [of this page]("http://unix.stackexchange.com/questions/1670/how-can-i-use-ffmpeg-to-split-mpeg-video-into-10-minute-chunks")

guy offers this solution which works on the sampled aac-container files ALTHO not totally same size but split and not reencoded
I do not know which degree of accuracy you wish for here ex : I got 4 splits on a 4-minute   and they were 1.00 0.59 0.55 1.00


so maybe try it  ;   maybe "please" Master :grin: we are not worthy :grin:  Fake will fine-tune it for us if finetunable



```
ffmpeg -i input.aac" -c copy -map 0 -segment_time 1800 -f segment output%03d.aac
```

---

### Post by ron998 on 2015-11-10
> **shantiq said:**
> ... try it...
Thanks Shantiq
This does the job.
```
ffmpeg -i filename.aac -f segment -segment_time 1800 -c copy filename_%03d.aac
```
filename_000.aac 
filename_001.aac 
filename_002.aac 
filename_003.aac
etc.

---

### Post by Yellow Pasque on 2015-11-10
> **andrew.46 said:**
> I have not tried it (and it will need wine) but the developer of qaac also has an aac cutter:

[https://github.com/nu774/m4acut](https://github.com/nu774/m4acut)

which might be worth a look?

Thank you! m4acut is what I have been looking for. It does not require wine. The only quirk is that you can't split out multiple tracks with one command like you can with mp3splt, but otherwise, it is a handy utility.

---

