---
title: "Extract audio from mp4"
date: 2009-04-11
forum: Multimedia Software
---

### Post by davidbilla on 2009-04-11
I have an mp4 video from which I want to extract only a part of the audio - say, from 00:05:00 to 00:07:00 - and save it as an mp3 with a bitrate of 128 kbps or less. How can I go about doing it?

Thanks.

---

### Post by davidbilla on 2009-04-11
Hello...? I hope the information given above is enough. 

Can extraction of audio from an mp4 file be done with, for example, ffmpeg? If yes, how?

---

### Post by FakeOutdoorsman on 2009-04-11
First you may need prepare FFmpeg to enable the restricted encoders:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Intrepid Ibex and above:
```
ffmpeg -ss 00:05:00:00 -t 00:02:00:00 -i input.mp4 -acodec libmp3lame -ab 128k output.mp3
```
Hardy Heron:
```
ffmpeg -ss 00:05:00:00 -t 00:02:00:00 -i input.mp4 -ab 128k output.mp3
```
[indent]**ss:** time offset from beginning of input in hh:mm:ss:frames.
**t:** duration of encode
**ab:** audio bitrate[/indent]

---

### Post by u-slayer on 2009-04-11
mplayer -quiet file.mp4 -ao pcm:fast:file=output.wav -vc dummy -vo null -channels 2 -ss 5:00 -endpos 2:00

---

### Post by leifw on 2009-04-12
I couldn't get the ffmpeg command to work because it kept complaining that libmp3lame was an unknown encoder.  However, using the mplayer command to extract a wave and then lame to encode that to an mp3 worked for me.

Thanks to both of the posters who offered an answer.

Leif

---

### Post by FakeOutdoorsman on 2009-04-12
> **leifw said:**
> I couldn't get the ffmpeg command to work because it kept complaining that libmp3lame was an unknown encoder.
What version of Ubuntu are you using?

---

### Post by octavianus on 2009-07-07
Keep it simple.It is a very easy process with "Sound Converter" which is available in the repository. Just drop the mp4 file(s) in  the Sound Converter dialogue box and convert it in to Mp3 , ogg or AAC whatever you prefer.

---

### Post by rossmoore on 2009-07-07
I agee with octavianus unless you want to do a whole batch of these files. I think sound Converter will only let you rip the whole file, not just the minutes you specified.

Another, more flexible, option is to use avidemux (in the respositories). It takes a few moments to figure out how to use it (happy to help if you have trouble), but you should be able set the start and end times (using the tool to help you visually pick the right moments in the video) and rip the audio to a file in the format of your choosing.

---

### Post by JugglinPhil on 2009-10-12
> **octavianus said:**
> Keep it simple.It is a very easy process with "Sound Converter" which is available in the repository. Just drop the mp4 file(s) in  the Sound Converter dialogue box and convert it in to Mp3 , ogg or AAC whatever you prefer.
+1
Tried it and worked just fine, to get the part you want you can edit the resulting audio file in Audacity, its pretty simple.

---

### Post by vinutux on 2009-10-12
convert to mp3 with "sound conveter"

open it in "audacity" 

play it and deleted unwanted portions & save it as mp3

---

### Post by bonfire89 on 2009-11-11
sound converter worked for me.

---

### Post by bviktor on 2009-12-30
> **vinutux said:**
> convert to mp3 with "sound conveter"

open it in "audacity" 

play it and deleted unwanted portions & save it as mp3

that's a really "great" solution. first lose quality by converting the original audio track of the video to mp3, and then compress it once again with audacity. yes, the other "solutions" provided here will also result in unnecessary quality loss.

is there any solution to extract the original aac audio without doing such silly conversions? no, extracting to wav and then encoding the already lossy audio (hint: it won't become lossless just because it's converted to wav) to a lossy/lossless format is **not** a solution

---

### Post by bviktor on 2009-12-30
solution:

[http://www.afterdawn.com/software/video_software/video_tools/yamb.cfm](http://www.afterdawn.com/software/video_software/video_tools/yamb.cfm)

- install with mp4box
- run, editing/click to extract streams
- add input mp4
- select audio track (aac)
- select mp4 output (in raw format you won't be able to seek)
- set output folder to something else than the original mp4

a linux solution would be handy, but i couldn't find one yet. i think it will run with wine but i haven't tested it.

useful pages:

[http://forums.macrumors.com/showthread.php?t=224949](http://forums.macrumors.com/showthread.php?t=224949)

especially this post:

[http://forums.macrumors.com/showpost.php?p=7101279&postcount=19](http://forums.macrumors.com/showpost.php?p=7101279&postcount=19)

and:

[http://www.afterdawn.com/guides/archive/how_to_edit_aac_mp4_audio_page_2.cfm](http://www.afterdawn.com/guides/archive/how_to_edit_aac_mp4_audio_page_2.cfm)

---

### Post by ethanay on 2010-02-14
try this:
[http://ubuntuforums.org/showthread.php?p=8823611#post8823611](http://ubuntuforums.org/showthread.php?p=8823611#post8823611)

---

### Post by FernandoDaniel on 2010-03-21
I am really shocked, at my desktop I am used to look for applications on Internet or at dealers and then I have to be sure that configuration is appropiated to run the application (a whole mess).

But with Ubuntu is completely different: meanning, easy, fast and every single application is like the OS itself, completely light (no HD or RAM or excessive cache demanding).

I have installed the AudioConverter and have converted some mp4 files on mp3, faster than it takes me to registrate to the Forum in order to comment.

However, I have tried also to convert flv files, without success. If there any "secret" to do it, I would appreciate to know it.

I have read this can be made using Utube ripper, but I just want to know the options, as a new Ubuntu user.
Fer

---

### Post by Pluto86 on 2010-10-24
You can use MP4Box to extract the audio or video without the need to re-encode it.

To install MP4Box:
```
 sudo apt-get install gpac
```To view the tracks in the mp4:
```
 MP4Box -info file.mp4
```Output:
```
* Movie Info *
    Timescale 600 - Duration 00:03:58.858
    Fragmented File no - 2 track(s)
    File Brand mp42 - version 0
    Created: GMT Sat Oct 16 23:46:24 2010

File has root IOD
Scene PL 0xff - Graphics PL 0xff - OD PL 0xff
Visual PL: AVC/H264 Profile (0x15)
Audio PL: AAC Profile @ Level 2 (0x29)
No streams included in root OD

iTunes Info:

Track # 1 Info - TrackID 1 - TimeScale 1000 - Duration 00:03:58.859
Media Info: Language "Undetermined" - Type "vide:avc1" - 5727 samples
MPEG-4 Config: Visual Stream - ObjectTypeIndication 0x21
AVC/H264 Video - Visual Size 1280 x 720 - Profile High @ Level 3.1
NAL Unit length bits: 32
Pixel Aspect Ratio 1:1 - Indicated track size 1280 x 720
Self-synchronized

Track # 2 Info - TrackID 2 - TimeScale 44100 - Duration 00:03:58.840
Media Info: Language "Undetermined" - Type "soun:mp4a" - 10286 samples
MPEG-4 Config:Audio Stream - ObjectTypeIndication 0x40
MPEG-4 Audio AAC LC - 2 Channel(s) - SampleRate 44100
Synchronized on stream 1
```To extract the audio (in my case Track# 2):
```
 MP4Box -raw 2 file.mp4
```

---

### Post by hamidvosugh on 2010-10-25
> **octavianus said:**
> Keep it simple.It is a very easy process with "Sound Converter" which is available in the repository. Just drop the mp4 file(s) in  the Sound Converter dialogue box and convert it in to Mp3 , ogg or AAC whatever you prefer.
The easiest way ever
You might also need the following to convert to mp3
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse

---

### Post by thomas_d_j on 2011-04-26
To extract the **actual audio track as-is** (no re-encoding),

(1) First find out what format the sound track is in (you need to know this to help choose the correct file extension in step 2):

```
ffmpeg -i my_video.mp4
```

There should be a line in the output which identifies the audio codec, something like:

*Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16, 125 kb/s*

(2) Then to extract the audio:

```
ffmpeg -i my_video.mp4 -vn -acodec copy my_audio.m4a
```

Thanks to Howard Pritchett for his howto at [http://howto-pages.org/ffmpeg/](http://howto-pages.org/ffmpeg/)

---

### Post by beew on 2011-04-26
Don't know about sound converter, there is a very easy to use program called WINFF which is basically ffmpeg with a GUI. It works for me (or you can use ffmpeg on the terminal) I think it does batch conversion as well.

---

### Post by secros on 2011-08-19
Just wanna bump this from a while ago.  Needed to pull aac from mp4s (a lot of them in a recursive way).  Sound converter makes quick work of the recursive conversion from aac to mp3, but I really had no reason to convert.  AAC was just fine with me.  

> ffmpeg -i my_video.mp4 -vn -acodec copy my_audio.m4a

worked perfectly once i changed it for aac.  Thanks, thomas_d_j.

---

### Post by dniMretsaM on 2011-08-19
I use VLC (you can choose any supported output, not just MP3): [URL="http://www.howtogeek.com/howto/2719/how-to-convert-video-files-formats-to-mp3-with-vlc/"]http://www.howtogeek.com/howto/2719/how-to-convert-video-files-formats-to-mp3-with-vlc/
[/URL]

---

