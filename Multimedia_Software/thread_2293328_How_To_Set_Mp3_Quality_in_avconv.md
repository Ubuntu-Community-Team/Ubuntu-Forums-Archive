---
title: "How To Set Mp3 Quality in avconv?"
date: 2015-09-04
forum: Multimedia Software
---

### Post by johny why on 2015-09-04
hi

the utility avconv has a codec-specific quality option "-aq". i cannot find documentation for allowed values for Mp3 output. I'm trying to convert from mp4 video to mp3 audio.

this helpfile doesn't explain this, that i can see:
[https://libav.org/avconv.html](https://libav.org/avconv.html)

maybe i misunderstood.

can anyone refer me to documentation on this?

would it be the same quality settings listed here?
[https://trac.ffmpeg.org/wiki/Encode/MP3](https://trac.ffmpeg.org/wiki/Encode/MP3)
> the range is 0-9 where a lower value is a higher quality

confused-- somebody here is using "-aq 128k"
[http://www.stackoverflow.dluat.com/questions/23061126/unwelcome-delay-when-using-arecord-with-aconv](http://www.stackoverflow.dluat.com/questions/23061126/unwelcome-delay-when-using-arecord-with-aconv)

thx~

---

### Post by mc4man on 2015-09-04
likely any of these would work
```
avconv -i  input-file -codec:a libmp3lame -aq 2 output.mp3

avconv -i  input-file -codec:a libmp3lame -q:a 2 output.mp3

avconv -i  input-file -c:a libmp3lame -aq 2 output.mp3

avconv -i  input-file -c:a libmp3lame -q:a 2 output.mp3
```

---

### Post by ajgreeny on 2015-09-04
You can also set a specific bitrate if you wish with, for example ```
avconv -i file.flac -acodec libmp3lame -ab 320k file.mp3
```which not surprisingly will give you a bitrate of 320kb/s

The command that mc4man shows will, however, probably give a better variable bitrate quality; the -aq figures go from 1 for the best to 9 for the lowest and 6 is often good enough for general listening or recordings of speech, but with storage space being so cheap these days why not go for a better quality.

Try a few to see if the differences matter to you.

---

### Post by johny why on 2015-09-04
> **ajgreeny said:**
> ```
avconv -i file.flac -acodec libmp3lame -ab 320k file.mp3
```which not surprisingly will give you a bitrate of 320kb/s
i'm not seeing "-ab" in the man page i linked, nor in "avconv -h". Is it documented someplace?

also, there's another option, '-b', which is for bitrate, right? Wouldn't that potentially conflict?

also, no point trying to make my ouput bitrate higher than the input bitrate, right?

> **ajgreeny said:**
> the -aq figures go from 1 for the best to 9 for the lowest
so, not down to 0 for best, as with ffmpeg? (see link in op)

> **ajgreeny said:**
> with storage space being so cheap these days why not go for a better quality. Try a few to see if the differences matter to you.
yeah, i just want to set highest quality and forgetaboutit, and not bother with listening tests. 


[hr][/hr]wrt that, i want 2-pass vbr-- can avconv do that? in that man page, i'm seeing the following under 'private options'. Is this all i need to get 2-pass?
> ‘-stats string’ - Filename for 2 pass stats.(answered here, you have to run avconv twice with the -pass option [http://askubuntu.com/questions/231192/2-pass-encoding-with-avconv]("http://askubuntu.com/questions/231192/2-pass-encoding-with-avconv"))



[hr][/hr]Hm, problem with 2-pass, i'm getting:
> 
$ avconv -vn -y -i "movie.mp4" -pass 1  /dev/null
avconv version 9.18-6:9.18-0ubuntu0.14.04.1, Copyright (c) 2000-2014 the Libav developers
  built on Mar 16 2015 13:19:10 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Current Value - Running.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: isommp42
    creation_time   : 2015-02-07 18:18:58
  Duration: 00:06:02.11, start: 0.000000, bitrate: 656 kb/s
    Stream #0.0(und): Video: h264 (High), yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 462 kb/s, 29.97 fps, 29.97 tbr, 30k tbn, 59.94 tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, fltp, 191 kb/s
    Metadata:
      creation_time   : 2015-02-07 18:18:59
**Unable to find a suitable output format for '/dev/null'**


[hr][/hr]i'm not specifiying codec at all. Is that important? i'm getting an mp3 output file with:
> $ avconv -vn -aq 0 -i "movie.mp4" "audio.mp3"
answered here:
> ‘-f fmt (input/output)’ - Force input or output file format. The format is normally autodetected for input files and guessed from file extension for output files, so this option is not needed in most cases.
[https://libav.org/avconv.html](https://libav.org/avconv.html)
thx!

---

### Post by ajgreeny on 2015-09-04
> i'm not seeing "-ab" in the man page i linked, nor in "avconv -h". Is it documented someplace?

also, there's another option, '-b', which is for bitrate, right? Wouldn't that potentially conflict?

also, no point trying to make my ouput bitrate higher than the input bitrate, right?
Interesting point and I have a nasty suspicion you're right about the -ab option as I've just looked and can't find it either, but having just used it without any errors to make a mp3 file at both bitrates, it has apparently worked, and mediainfo reports the two output files as being at either the 320 or 128 kb/s.

I am baffled!  And with "man avconv" being 5672 lines in length it is not exactly easy reading.  Perhaps you need to wait for an avconv expert to come along and answer.

You are absolutely right, however, about the quality of the input file being the limiting factor, and there being no point in turning a 128kb/s file into a 320kb/s file.

---

### Post by johny why on 2015-09-04
i wonder if -ab is a shorthand for "audio bitrate".

any ideas about my issue, above, re 2-pass?

also, is 0 not best quality?

thx!

---

### Post by andrew.46 on 2015-09-05
> **ajgreeny said:**
> The command that mc4man shows will, however, probably give a better variable bitrate quality; the -aq figures go from 1 for the best to 9 for the lowest and 6 is often good enough for general listening or recordings of speech, but with storage space being so cheap these days why not go for a better quality.

Mind you conventional wisdom is that rather than use a high bitrate mp3 (of the 320k type) you should use a *lossless* format such as flac, alac or wavpack... Then the argument that 'storage space is cheap' has very real meaning. I am in the process of converting my music to alac (via qaac and abcde) for this reason.

---

### Post by johny why on 2015-09-05
> **andrew.46 said:**
> you should use a *lossless* format such as flac, alac or wavpack... Then the argument that 'storage space is cheap' has very real meaning. 
Thank you very much for this superb info. My current purpose is Android playback, which i believe those formats can't do. But i'm always on a quest for holy grail formats. i appreciate it.

---

### Post by andrew.46 on 2015-09-05
> **johny why said:**
> Thank you very much for this superb info. My current purpose is Android playback, which i believe those formats can't do. But i'm always on a quest for holy grail formats. i appreciate it.

I am a little out of touch with Android but from dim memory vlc runs on Android, and this should be able to playback many of the codecs I have mentioned. But I have been wrong before :)

---

### Post by shantiq on 2015-09-05
> **johny why said:**
> i wonder if -ab is a shorthand for "audio bitrate".

any ideas about my issue, above, re 2-pass?

also, is 0 not best quality?

thx!


-ab   became -b:a   a while back in avconv as in ffmpeg   so easiest conversion goes thus:

```
avconv -i input.flac -b:a 320k output.mp3
```


it knows to use the right codec for mp3 ;   and change 320 for 64,128,156,192,224,256,   to suit your wish    does the same as -q in effect
[FONT=comic sans ms]**change flac for mp4 in your case**[/FONT]


IF you want to do a [FONT=comic sans ms]**bulk conversion**[/FONT] place them all in one folder and run this:

```
for f in *.flac; do avconv -i "$f" -b:a 320k  "${f%.flac}.mp3"; done
```

---

### Post by Yellow Pasque on 2015-09-05
> **johny why said:**
> Thank you very much for this superb info. My current purpose is Android playback, which i believe those formats can't do.

Android 3.1 added native FLAC support: [https://developer.android.com/guide/appendix/media-formats.html](https://developer.android.com/guide/appendix/media-formats.html)

---

### Post by SeijiSensei on 2015-09-05
The default music players on my Android phones have always played FLAC and Ogg Vorbis natively, including my now three-year-old Samsung S3.  FLAC is the only format I've used for music archiving for the past few years.  MX Player for Android covers all the bases when it comes to video playback including things like 10-bit H.264 and H.265 ("hevc") encodes, though the latter probably only works with the software decoder.

I'd avoid proprietary formats like WMA, but anything open like FLAC, Matroska, etc., plays fine on Android just like they do on Linux systems.  I'd give the native formats a try before getting into re-encoding.

---

### Post by johny why on 2015-09-05
> **andrew.46 said:**
> vlc runs on Android, and this should be able to playback many of the codecs I have mentioned.
thx for that! but i also have to save space on my droid. Will reserve those uncompressed formats for my pc. 

> **shantiq said:**
> change 320 for 64,128,156,192,224,256,   to suit your wish    does the same as -q in effect
was wondering about that. What happens if quality and bitrate conflict with each other?

anyone know if best quality is 1 or 0?

Main unanswered question now, the error i'm getting on 2-pass. Posted here:
[http://ubuntuforums.org/showthread.php?t=2293537](http://ubuntuforums.org/showthread.php?t=2293537)

thx

---

### Post by shantiq on 2015-09-05
only use one at a time

---

### Post by SeijiSensei on 2015-09-06
> **johny why said:**
> thx for that! but i also have to save space on my droid. Will reserve those uncompressed formats for my pc. 
I use a memory card on my phones.  Both my old S3 and my new LG Stylo support cards.  Even 32 GB holds a lot of music.

---

### Post by johny why on 2015-09-06
> **SeijiSensei said:**
> I use a memory card on my phones.  Both my old S3 and my new LG Stylo support cards.  Even 32 GB holds a lot of music.

Thx, i know about memory cards. I use one in my phone. 

thx

---

