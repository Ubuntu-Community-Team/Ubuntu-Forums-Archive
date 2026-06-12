---
title: "Trying to convert video over using ffmpeg - says Im missing something"
date: 2012-04-20
forum: Multimedia Software
---

### Post by AlexOnVinyl on 2012-04-20
Here's basically what I did:

```
alex@griever:~/Videos$ ffmpeg -i Immortals720x264.mkv -vcodec mpeg4 -qscale 2 -acodec libmp3lame -aq 3 output.mp4
```

Here's what I got:
> 
ffmpeg version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Mar 22 2012 05:29:10 with gcc 4.6.3
This program is not developed anymore and is only provided for compatibility. Use avconv instead (see Changelog for the list of incompatible changes).
[matroska,webm @ 0x9b9a240] max_analyze_duration reached
[matroska,webm @ 0x9b9a240] Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 180000.00 (180000/1) -> 23.98 (24000/1001)
Input #0, matroska,webm, from 'Immortals720x264.mkv':
  Metadata:
    title           : Immortals720x264
  Duration: 01:50:26.78, start: 0.000000, bitrate: 448 kb/s
    Stream #0.0(eng): Video: h264 (High), yuv420p, 1280x690 [PAR 1:1 DAR 128:69], 23.98 fps, 23.98 tbr, 1k tbn, 180k tbc (default)
    Stream #0.1(eng): Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s (default)
    Stream #0.2(eng): Subtitle: [0][0][0][0] / 0x0000 (default)
[buffer @ 0x9ebeb20] w:1280 h:690 pixfmt:yuv420p
Output #0, mp4, to 'output.mp4':
    Stream #0.0(eng): Video: mpeg4, yuv420p, 1280x690 [PAR 1:1 DAR 128:69], q=2-31, 200 kb/s, 90k tbn, 23.98 tbc (default)
    Stream #0.1(eng): Audio: libmp3lame, 48000 Hz, 5.1, s16, 200 kb/s (default)
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height


What all am I missing?

---

### Post by ron999 on 2012-04-20
> **AlexOnVinyl said:**
> 

What all am I missing?

Hi 
The audio track is 5.1 channels.
It needs to be 2 channels for mp3.
Add [COLOR="Red"]-ac 2[/COLOR] to the command like this:-
```
ffmpeg -i Immortals720x264.mkv -vcodec mpeg4 -qscale 2 -acodec libmp3lame -aq 3 [COLOR="Red"]-ac 2[/COLOR] output.mp4
```

---

### Post by AlexOnVinyl on 2012-04-21
> **ron999 said:**
> Hi 
The audio track is 5.1 channels.
It needs to be 2 channels for mp3.
Add [COLOR="Red"]-ac 2[/COLOR] to the command like this:-
```
ffmpeg -i Immortals720x264.mkv -vcodec mpeg4 -qscale 2 -acodec libmp3lame -aq 3 [COLOR="Red"]-ac 2[/COLOR] output.mp4
```

Please look at my other thread: [http://ubuntuforums.org/showthread.php?t=1962378]("http://ubuntuforums.org/showthread.php?t=1962378")

---

### Post by AlexOnVinyl on 2012-04-21
Wow - that was my first script it actually worked!! Thank you

---

### Post by ron999 on 2012-04-21
```
ffmpeg -i Immortals720x264.mkv -vcodec mpeg4 -qscale 2 -acodec libmp3lame -aq 3 [COLOR="Red"]-ac 2[/COLOR] output.mp4
```
If this command gives a good result, it's OK to make your own preset for WinFF. :cool:
Howto is here ---> [http://code.google.com/p/winff/wiki/HowToMakePresets]("http://code.google.com/p/winff/wiki/HowToMakePresets")

---

### Post by AlexOnVinyl on 2012-04-23
> **ron999 said:**
> ```
ffmpeg -i Immortals720x264.mkv -vcodec mpeg4 -qscale 2 -acodec libmp3lame -aq 3 [COLOR="Red"]-ac 2[/COLOR] output.mp4
```
If this command gives a good result, it's OK to make your own preset for WinFF. :cool:
Howto is here ---> [http://code.google.com/p/winff/wiki/HowToMakePresets]("http://code.google.com/p/winff/wiki/HowToMakePresets")

My only issue now is setting the file size, is there a way I can set the file size to something more fitting instead of a whopping 3GBs?

---

### Post by mimihu88 on 2012-04-23
> **AlexOnVinyl said:**
> My only issue now is setting the file size, is there a way I can set the file size to something more fitting instead of a whopping 3GBs?

1. -aq=audio_bitrate,I don't think your setting "-aq 3" is valid,should be something like "-aq 192k", I found ffmpeg is using 200k by default refer to what you got.
2. output_size
In my experience, it depends on the "bitrate",you can calculate before converting
> duration(seconds) * ( video_bitrate + audio_bitrate) / (8*1024) = size [MB]

```
ffmpeg -i input -c:v libx264 -b:v video_bitrate -c:a libvo_aacenc -aq audio_bitrate -ac 2 output.mp4
```

---

### Post by FakeOutdoorsman on 2012-04-23
> **AlexOnVinyl said:**
> My only issue now is setting the file size, is there a way I can set the file size to something more fitting instead of a whopping 3GBs?

There are two major methods of setting the quality of your output: *-b* and *-qscale* (or *-crf* when using libx264 and perhaps libvpx). When you want the output to be a certain "quality" and don't really care what the file size will be then use *-qscale*. It is the option to use when quality is the important factor. Generally you use the highest value that still gives an acceptable quality. 2-5 is usually a good range to try.

When file size is more important than a certain quality then use *-b*. Example: a 10 minute (600 second) input with a desired output file size of 250 MB:
> file size / duration = bitrate
(250 MB * 8192 [converts MB to kilobits]) / 600 seconds = ~3413 kilobits per second for the whole file.
Splitting the bitrate between video and audio is easy. If you want the audio to take up to 128 kb/s:
> ~3413 total bitrate - **128** kb/s desired audio bitrate = **3285** kb/s video bitrate.
These numbers then get entered into your command:
```
ffmpeg -i input -b:v 3285k -b:a 128k output
```
Same as above, but using older syntax (depending on your ffmpeg version):
```
ffmpeg -i input -b 3285k -ab 128k output
```
This doesn't mean that the output will be exactly 250 MB, but it will be close enough. Some encoders benefit from performing two-passes when using *-b*:
```
ffmpeg -i input -b:v 3285k -an -pass 1 output
ffmpeg -i input -b:v 3285k -b:a 128k -pass 2 -y output

```
Personally, I don't really care about file size more than quality, so I never really use this method.

---

### Post by AlexOnVinyl on 2012-04-23
> **FakeOutdoorsman said:**
> There are two major methods of setting the quality of your output: *-b* and *-qscale* (or *-crf* when using libx264 and perhaps libvpx). When you want the output to be a certain "quality" and don't really care what the file size will be then use *-qscale*. It is the option to use when quality is the important factor. Generally you use the highest value that still gives an acceptable quality. 2-5 is usually a good range to try.

When file size is more important than a certain quality then use *-b*. Example: a 10 minute (600 second) input with a desired output file size of 250 MB:

Splitting the bitrate between video and audio is easy. If you want the audio to take up to 128 kb/s:

These numbers then get entered into your command:
```
ffmpeg -i input -b:v 3285k -b:a 128k output
```
Same as above, but using older syntax (depending on your ffmpeg version):
```
ffmpeg -i input -b 3285k -ab 128k output
```
This doesn't mean that the output will be exactly 250 MB, but it will be close enough. Some encoders benefit from performing two-passes when using *-b*:
```
ffmpeg -i input -b:v 3285k -an -pass 1 output
ffmpeg -i input -b:v 3285k -b:a 128k -pass 2 -y output

```
Personally, I don't really care about file size more than quality, so I never really use this method.

In my case, I don't own a Boxee Media Box yet, so using my PS3 and having to only be able to support FAT32 - which only goes up to 4GB a file as far as transferring goes, I'm left with either streaming or reducing size.  

Here's an example:

> Complete name                            : /home/alex/Videos/A.Clockwork.Orange.1971.720p.BluRay.x264-/A.Clockwork.Orange.1971.720p.BluRay.x264-.mkv
Format                                   : Matroska
Format version                           : Version 2
File size                                : 2.42 GiB
Duration                                 : 2h 16mn
Overall bit rate                         : 2 534 Kbps
Movie name                               : A.Clockwork.Orange.1971.720p.BluRay.x264-
Encoded date                             : UTC 2012-04-02 12:33:39
Writing application                      : mkvmerge v2.9.7 ('Tenderness') built on Jul  5 2009 13:26:28
Writing library                          : libebml v0.7.8 + libmatroska v0.8.1

Video Settings:

> 
Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L4.1
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 8 frames
Codec ID                                 : V_MPEG4/ISO/AVC
Duration                                 : 2h 16mn
Bit rate                                 : 2 084 Kbps
Width                                    : 1 280 pixels
Height                                   : 720 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Variable
Frame rate                               : 23.976 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.094
Stream size                              : 1.94 GiB (80%)
Writing library                          : x264 core 120

Language                                 : English
Default                                  : Yes
Forced                                   : No
Color primaries                          : BT.709-5, BT.1361, IEC 61966-2-4, SMPTE RP177
Transfer characteristics                 : BT.709-5, BT.1361
Matrix coefficients                      : BT.709-5, BT.1361, IEC 61966-2-4 709, SMPTE RP177

Audio Settings

> 

Audio
ID                                       : 2
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Mode extension                           : CM (complete main)
Codec ID                                 : A_AC3
Duration                                 : 2h 16mn
Bit rate mode                            : Constant
Bit rate                                 : 448 Kbps
Channel(s)                               : 6 channels
Channel positions                        : Front: L C R, Side: L R, LFE
Sampling rate                            : 48.0 KHz
Bit depth                                : 16 bits
Compression mode                         : Lossy
Stream size                              : 438 MiB (18%)
Language                                 : English
Default                                  : Yes
Forced                                   : No

Text
ID                                       : 3
Format                                   : UTF-8
Codec ID                                 : S_TEXT/UTF8
Codec ID/Info                            : UTF-8 Plain Text
Language                                 : English
Default                                  : Yes
Forced                                   : No


back when I used to use Winblows - I used a program called GordianKnot to be able to determine what I wanted to do with a program, sadly it was all GUI.

In this case - I want to take my "Clockwork Orange" movie and maintain its 720p quality but shrink it down to about 2GB or 1.8GB - I want to convert it from Matroska to MP4 or the outdated AVI - the only issue is I don't know how to go about it. I know how to do a straight convert from MKV to MP4 - and replace a few video codecs and audio codecs but I want to limit the FileSize to no bigger than a certain amount.

---

### Post by shantiq on 2012-04-24
your best tool for this would be [**==> HANDBRAKE**]("http://ubuntuforums.org/showpost.php?p=11535798&postcount=2") probably easier from the GUI  but

you can use 


> HandBrakeCLI -i infile.mkv -o outfile.mp4 -e ffmpeg4 -b 3000 -E ac3 -B 192 -r 30

here your size control is -b 3000   the size of the video in kbps   hike it to 7000 and it is huge   take it down to say 1200 and much smaller    a DVD is usually 9000k or thereabouts;   so you can really control it there for what you want 



all options clearly shown on ```
HandBrakeCLI -help
```


from a DVD   for example


> HandBrakeCLI -i /dev/cdrom -o outfile.mkv -e ffmpeg4 -b 3000 -E ac3 -B 192 -r 30 -s 1,2,3 --subtitle-default 2



This is what it looks like in gui version

[ATTACH]216501[/ATTACH]



**PS** Having said all this  mkv is my favourite wrapper/format   it is very stable and plays on everything in my experience


 [img]http://img838.imageshack.us/img838/5745/smilie33.png[/img][img]http://img838.imageshack.us/img838/5745/smilie33.png[/img]

---

### Post by AlexOnVinyl on 2012-04-24
> **shantiq said:**
> your best tool for this would be [**==> HANDBRAKE**]("http://ubuntuforums.org/showpost.php?p=11535798&postcount=2") probably easier from the GUI  but

you can use 




here your size control is -b 3000   the size of the video in kbps   hike it to 7000 and it is huge   take it down to say 1200 and much smaller    a DVD is usually 9000k or thereabouts;   so you can really control it there for what you want 



all options clearly shown on ```
HandBrakeCLI -help
```


from a DVD   for example






This is what it looks like in gui version

[ATTACH]216501[/ATTACH]



**PS** Having said all this  mkv is my favourite wrapper/format   it is very stable and plays on everything in my experience


 [img]http://img838.imageshack.us/img838/5745/smilie33.png[/img][img]http://img838.imageshack.us/img838/5745/smilie33.png[/img]


I've used Handbrake before the only issue I have with it is the .m4v contain as opposed to the .mp4 that the previous versions of it had.  I use to use the older versions on a Windows Environment.

Also:

> **shantiq said:**
>  

**PS** Having said all this  mkv is my favourite wrapper/format   it is very stable and plays on everything in my experience 

This is untrue for the Sony Playstation 3.  MKV is only supported through CFW which I do not have or condone.

---

