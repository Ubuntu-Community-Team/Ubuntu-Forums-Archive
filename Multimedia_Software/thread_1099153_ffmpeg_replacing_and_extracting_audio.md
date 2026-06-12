---
title: "ffmpeg replacing and extracting audio"
date: 2009-03-17
forum: Multimedia Software
---

### Post by Tyler C on 2009-03-17
Hello!

I want to extract the audio from my video, clean it up with audacity, then replace the audio in the video. What are the ffmpeg commands to do this?

---

### Post by FakeOutdoorsman on 2009-03-18
I can give you general commands, but it will be easier if you let me know the specifics of your video.  Paste the result of:
```
ffmpeg -i yourinputvideo.mp4
```

---

### Post by Tyler C on 2009-03-18
```
ffmpeg -i out-1.ogv
[theora @ 0xb7e382f0]Theora bitstream version 30201
[theora @ 0xb7e382f0]560 bits left in packet 81
[theora @ 0xb7e382f0]7 bits left in packet 82
Input #0, ogg, from 'out-1.ogv':
  Duration: 00:00:10.4, start: 0.000000, bitrate: 1161 kb/s
    Stream #0.0: Invalid Codec type -1
    Stream #0.1: Video: theora, yuv420p, 848x640 [PAR 1:1 DAR 53:40], 15.00 tb(r)
    Stream #0.2: Audio: vorbis, 22050 Hz, mono, 89 kb/s

```

---

### Post by FakeOutdoorsman on 2009-03-18
Extract the audio:
```
ffmpeg -i out-1.ogv -acodec copy -vn audio.ogg
```
Enter the new audio:
```
ffmpeg -i out-1.ogv -i audio.ogg -map 0:1 -map 1:0 -vcodec copy -acodec copy everything.ogg
```

---

### Post by me13221 on 2009-03-19
This doesn't work for me- it gives me the error:

Output #0, avi, to 'mvi.avi':
    Stream #0.0: Video: mpeg4, yuv420p, 320x240 [PAR 0:1 DAR 0:1], q=2-31, 30.00 tb(c)
    Stream #0.1: Audio: libmp3lame, 11025 Hz, mono, 16 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #1.0 -> #0.1
Press [q] to stop encoding
error, non monotone timestamps 1 >= 0
av_interleaved_write_frame(): Error while opening file

It's picking the video from the first file (which is ffmpeg mpeg-4) and the audio from the second file. but it only gets through one frame and chokes.
?

---

### Post by FakeOutdoorsman on 2009-03-19
> **me13221 said:**
> This doesn't work for me- it gives me the error:

Output #0, avi, to 'mvi.avi':
    Stream #0.0: Video: mpeg4, yuv420p, 320x240 [PAR 0:1 DAR 0:1], q=2-31, 30.00 tb(c)
    Stream #0.1: Audio: libmp3lame, 11025 Hz, mono, 16 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #1.0 -> #0.1
Press [q] to stop encoding
error, non monotone timestamps 1 >= 0
av_interleaved_write_frame(): Error while opening file

It's picking the video from the first file (which is ffmpeg mpeg-4) and the audio from the second file. but it only gets through one frame and chokes.
?
What version of Ubuntu are you using?  Can you show your command and the full FFmpeg output?  Also give the output of:
```
ffmpeg -i secondfile.avi
```

---

### Post by sehrgut on 2009-03-24
Unfortunately, a known bug in ffmpeg with no agreed-upon fix upstream. Something to do with timestamp-interpolation code generating bad timestamps. *sigh* It's rather irksome that it doesn't even fail gracefully. It's especially bad with ogg, which doesn't require timestamps every frame.

---

### Post by aruseni on 2010-07-21
**[Recording and editing screencasts with recordMyDesktop and Audacity]("http://magic2lantern.blogspot.com/2010/07/recording-and-editing-screencasts-with.html")**

---

### Post by Epo Nym on 2012-03-02
When trying to split an audio file I ran into the same error.

After I did:

```

[FONT=Courier New]ffmpeg -ss [/FONT][FONT=Courier New]'00:18:26.8'[/FONT][FONT=Courier New] -t [/FONT][FONT=Courier New]'00:04:08.2'[/FONT][FONT=Courier New] -i fullaudio.mp3 -acodec copy audiofragment.mp3[/FONT]

```I got:

> [FONT=Courier New]
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.3, Copyright (c) 2000-2009 Fabrice Bellard, et al.

...

  built on Dec 21 2011 18:37:21, gcc: 4.4.3
[asf @ 0x9979a60]asf_read_pts **[COLOR=Red]failed[/COLOR]**
Input #0, asf, from 'fullaudio.mp3':
  Duration: 00:59:58.71, start: 0.413000, bitrate: 16 kb/s
    Stream #0.0: Audio: mp3, 11025 Hz, mono, s16, 16 kb/s
Output #0, mp3, to 'audiofragment.mp3':
    Stream #0.0: Audio: libmp3lame, 11025 Hz, mono, s16, 16 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
[NULL @ 0x9989560]**[COLOR=Red]error, non monotone timestamps[/COLOR]** -2695320 >= -2700000
av_interleaved_write_frame(): Error while opening file[/FONT]
Luckily I found a workaround. I made a full copy of the original file with ffmpeg, which presumably put the timestamps back in place. So I did:

```

[FONT=Courier New]ffmpeg -i fullaudio.mp3 -acodec copy tmp.mp3
ffmpeg -t '00:04:08.2' -ss '00:18:26.8' -i tmp.mp3 -acodec copy audiofragment.mp3
rm tmp.mp3[/FONT]

```Don't know if it works with other formats, however.

---

