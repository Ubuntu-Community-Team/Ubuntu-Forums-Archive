---
title: "oggenc says &quot;segmentation fault&quot;"
date: 2007-08-11
forum: Multimedia &amp; Video
---

### Post by hardmous on 2007-08-11
It happens every time.  Whenever I try to export to WAV in Audacity it crashes as well.  Also, whenever I try to rip a CD whatever app I'm using crashes.  I'm starting to see a pattern here.  i know there's some type of hardware issue with my computer, I just can't diagnose it?  Is this related?  I really need to solve this problem.  Thanks in advance.

---

### Post by hardmous on 2007-08-11
Anyone?

---

### Post by hardmous on 2007-08-12
Sorry to keep bumping this.  It's just that this is a very frustrating problem and I can't find help anywhere!

---

### Post by hardmous on 2007-08-13
Hello??

---

### Post by hardmous on 2007-08-16
Is this post ******* invisible or something?

---

### Post by RomeReactor on 2007-08-17
Hi. Your thread is the only one that comes up searching for "oggenc segmentation fault", so it is possible no-one else has come across your particular problem and thus haven't answered. Try reinstalling **vorbis-tools**:
```
sudo apt-get remove --purge vorbis-tools
```
then
```
sudo apt-get update
```
and
```
sudo apt-get install vorbis-tools
```

---

### Post by shaggy999 on 2008-03-29
I get this same problem when using certain encoding options:

```

brandon@ubuntu:~/Music/Steppenwolf/All Time Greatest Hits$ **oggenc --resample 32000 --bitrate 92 01\ -\ Born\ to\ Be\ Wild.flac**
Opening with flac module: FLAC file reader
Resampling input from 44100 Hz to 32000 Hz
Encoding "01 - Born to Be Wild.flac" to 
         "01 - Born to Be Wild.ogg" 
at approximate bitrate 92 kbps (VBR encoding enabled)
        [ 99.7%] [ 0m00s remaining] \ 

Done encoding file "01 - Born to Be Wild.ogg"

        File length:  3m 30.0s
        Elapsed time: 1m 02.6s
        Rate:         3.3663
        Average bitrate: 89.3 kb/s

**Segmentation fault (core dumped)**

```

I then run ogginfo on the encoded file and get this:

```

ogginfo *.ogg
Processing file "01 - Born to Be Wild.ogg"...

New logical stream (#1, serial: 69074827): type vorbis
Vorbis headers parsed for stream 1, information follows...
Version: 0
Vendor: Xiph.Org libVorbis I 20070622
Channels: 2
Rate: 32000

Nominal bitrate: 92.000000 kb/s
Upper bitrate not set
Lower bitrate not set
User comments section follows...
        TITLE=Born to Be Wild
        ARTIST=Steppenwolf
        TRACKNUMBER=1
        TRACKTOTAL=18
        ALBUM=All Time Greatest Hits
        MUSICBRAINZ_ALBUMID=42c7a245-6a3f-4800-b905-a8be1723615a
        MUSICBRAINZ_ALBUMARTISTID=12ff8858-bfcb-4812-a8dd-7e9debf0cbee
        MUSICBRAINZ_ARTISTID=12ff8858-bfcb-4812-a8dd-7e9debf0cbee
        MUSICBRAINZ_TRACKID=623828c2-648e-475d-a9b9-b2ff2c9be9dd
        MUSICBRAINZ_SORTNAME=Steppenwolf
        DISCID=0711cd12
        MUSICBRAINZ_DISCID=VCrb3XH2RaO9zmBR8vX6nAbGAMI-
**Warning: EOS not set on stream 1**
Vorbis stream 1:
        Total data length: 2347410 bytes
        Playback length: 3m:29.653s
        Average bitrate: 89.572725 kb/s

```

Note: What's weird is that the ogg file plays just fine as far as I can tell. But clearly it's malformated in some way.  I'm actually using this command to encode audio books, which are voice only. Hence the reason for the downsampling and low bitrate. Also, If I run oggenco like this:

```
oggenc -q4 file
```

I get NO segfault.

---

