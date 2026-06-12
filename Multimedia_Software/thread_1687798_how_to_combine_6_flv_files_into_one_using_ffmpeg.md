---
title: "how to combine 6 flv files into one using ffmpeg ?"
date: 2011-02-14
forum: Multimedia Software
---

### Post by shantiq on 2011-02-14
i wish to combine a few flv files into one using ffmpeg i have read around and still have not found a way    i need advice   thanx


here is the info on one of my files    they are all the same

```
Metadata:
    duration        : 543
    starttime       : 0
    totalduration   : 543
    width           : 384
    height          : 288
    videodatarate   : 420
    audiodatarate   : 116
    totaldatarate   : 544
    framerate       : 25
    bytelength      : 36930790
    canseekontime   : true
    sourcedata      : BD075F106MH1297669312307961
    purl            : 
    pmsg            : 
  Duration: 00:09:02.84, start: 0.000000, bitrate: 548 kb/s
    Stream #0.0: Video: h264, yuv420p, 384x288 [PAR 1:1 DAR 4:3], 430 kb/s, 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16, 118 kb/s

```

---

### Post by ron999 on 2011-02-14
Hi shantiq
I think that cat can be used with ffmpeg.
Like this:-
```
cat file1.flv file2.flv file3.flv file4.flv file5.flv file6.flv | ffmpeg -i - -vcodec copy -acodec copy final.flv
```
But I wouldn't trust it with flv files.

Might be better to use MP4Box and have an mp4 container.
Like this:-
```
MP4Box -add file1.flv -cat file2.flv -cat file3.flv -cat file4.flv -cat file5.flv -cat file6.flv final.mp4
```

---

### Post by cbanakis on 2011-02-14
I havent messed around with ffmpeg, but mkv files creator might work.

MKV-Files-Creator is in the ubuntu software center.

I use it to combine MKV and AVI's all the time.

Has a pretty nice GUI too.

All you need to do is load the 1st file, then select append and choose the next file, ect ect

The only consequence is that you will end up with an MKV file, and not a FLV.

I'll try to combine some flv's tonight when I get home, and let you know how it works out.

---

### Post by shantiq on 2011-02-14
commands do not work so far   quite confusing :KS:KS

---

### Post by andrew.46 on 2011-02-15
> **cbanakis said:**
> I havent messed around with ffmpeg, but mkv files creator might work.

MKV-Files-Creator is in the ubuntu software center.

I use it to combine MKV and AVI's all the time.


Hmmm.... do you mean mkvtoolnix or mkvmerge? I attach a screenshot demonstrating the append command. This will not work with all files.

---

### Post by shantiq on 2011-02-15
ok guys first of all **thanx** for your inputs but no dice so far:KS


====================================

the cat thing with ffmpeg seems to simply not work for me with **any** format   tried mkv mp4 flv

```
cat file1.flv file2.flv file3.flv file4.flv file5.flv file6.flv | ffmpeg -i - -vcodec copy -acodec copy final.flv

```

unless there is something i should change in the line


MP4Box is the best so far makes the file brilliantly but i end up with sound on only what were the first 2 sections
maybe needs fine-tuning command line instructions not sure what to do


i get   ```
MP4Box -add 1.mp4 -cat 2.mp4 -cat 3.mp4 -cat 4.mp4 -cat 5.mp4 -cat 6.mp4 final.mp4
IsoMedia import - track ID 1 - Video (size 384 x 288)
IsoMedia import - track ID 2 - Audio (SR 22050 - 2 channels)
Appending file 2.mp4                                      
[COLOR="Red"]No suitable destination track found - creating new one (type soun)[/COLOR]
Appending file 3.mp4                             
Appending file 4.mp4                             
Appending file 5.mp4                             
Appending file 6.mp4                             
Saving to final.mp4: 0.500 secs Interleaving
```

do not understand what file 2 is doing   same as the others insofar as i know

               ===================================
mkvmerge returns errors both on mkv and mp4   see image


============================================


**so** it looks as if the best route is MP4Box with fine-tuned commands

**Is there really** no way ffmpeg can handle this task?
it does not seem like a tall order

Anyway i keep trying   All suggestions welcome



shan

---

### Post by shantiq on 2011-02-15
ok the answer might lie here

Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '1.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    encoder         : Lavf52.64.2
  Duration: 00:10:01.02, start: 0.000000, bitrate: [COLOR="Red"]474 kb/s[/COLOR]
    Stream #0.0(und): Video: h264, yuv420p, 384x288 [PAR 1:1 DAR 4:3], 403 kb/s, 25 fps, 25 tbr, 50 tbn, 50 tbc
    Stream #0.1(und): Audio: aac, 22050 Hz, stereo, s16, [COLOR="Red"]67 kb/s[/COLOR]
At least one output file must be specified



Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '2.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    encoder         : Lavf52.64.2
  Duration: 00:10:01.07, start: 0.000000, bitrate: [COLOR="Red"]562 kb/s[/COLOR]
    Stream #0.0(und): Video: h264, yuv420p, 384x288 [PAR 1:1 DAR 4:3], 435 kb/s, 25 fps, 25 tbr, 50 tbn, 50 tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16, [COLOR="Red"]120 kb/s[/COLOR]
At least one output file must be specified


Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '3.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    encoder         : Lavf52.64.2
  Duration: 00:10:01.07, start: 0.000000, bitrate: [COLOR="Red"]491 kb/s[/COLOR]
    Stream #0.0(und): Video: h264, yuv420p, 384x288 [PAR 1:1 DAR 4:3], 419 kb/s, 25 fps, 25 tbr, 50 tbn, 50 tbc
    Stream #0.1(und): Audio: aac, 22050 Hz, stereo, s16, [COLOR="Red"]68 kb/s[/COLOR]



must be why i get problems      all these vids are from youtube ; segments of one documentary; they seem to have downloaded differently

so if i can homogenize them first then try MP4Box again or mkvmerge   :KS:KS:KS   God one needs to keep one's wits about one

---

### Post by cbanakis on 2011-02-15
> **andrew.46 said:**
> Hmmm.... do you mean mkvtoolnix or mkvmerge? I attach a screenshot demonstrating the append command. This will not work with all files.


Yeah, doesn't work.

Not even a little.

FLV no worky

Works great with most formats, but I guess flash is in its own category :(

---

### Post by andrew.46 on 2011-02-15
The FFmpeg FAQs have some answers:

[http://www.ffmpeg.org/faq.html#SEC27](http://www.ffmpeg.org/faq.html#SEC27)

---

### Post by shantiq on 2011-02-16
-removed-

---

### Post by shantiq on 2011-02-16
> **ron999 said:**
> Hi shantiq
I think that cat can be used with ffmpeg.
Like this:-
```
cat file1.flv file2.flv file3.flv file4.flv file5.flv file6.flv | ffmpeg -i - -vcodec copy -acodec copy final.flv
```
But I wouldn't trust it with flv files.

Might be better to use MP4Box and have an mp4 container.
Like this:-
```
MP4Box -add file1.flv -cat file2.flv -cat file3.flv -cat file4.flv -cat file5.flv -cat file6.flv final.mp4
```


Thanx Ron MP4Box finally did the trick

---

### Post by shantiq on 2011-02-16
**so to summarize**
   ===============



when wishing to turn a few flv files into one single video file


1.  ```
for f in *.flv; do ffmpeg -i "$f" -vcodec copy -acodec copy "${f%.flv}.mp4"; done
```


2.  ```
MP4Box -add 1.mp4 -cat 2.mp4 -cat 3.mp4 -cat 4.mp4 -cat 5.mp4 -cat 6.mp4   NameofNewCombinedFile.mp4
```

with as many con**cat**enated as one requires (here 6)

---

