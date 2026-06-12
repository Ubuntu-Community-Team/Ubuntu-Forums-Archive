---
title: "How to fix a video's audio track?"
date: 2011-03-22
forum: Multimedia Software
---

### Post by cfhowlett on 2011-03-22
Greetings:

So I've recorded some video in the field, i.e. outside, windy, noisy, etc.  I would like to strip out the audio, clean it up in Audacity and then repatriate it back to the video.  Video is in .mp4 format.  HOW TO PROCEED?  

By the way, film makers should feel free to upgrade my vocabulary.  I'm sure there's an industry term for what I described, but I don't know what that might be.

Thanks in advance.

---

### Post by cfhowlett on 2011-03-22
Greetings:

So I've recorded some video in the field, i.e. outside, windy, noisy, etc.  I would like to strip out the audio, clean it up in Audacity and then repatriate it back to the video.  HOW?  Video is in .mp4 format.

By the way, film makers should feel free to upgrade my vocabulary.  I'm sure there's an industry term for what I described, but I don't know what that might be.

Thanks in advance.

---

### Post by papibe on 2011-03-22
If your video uses regular codecs and container, you can use ffmpeg to extract both the audio and video tracks, and also to put them together again (I mean the improved audio).

Check this [tutorial]("http://howto-pages.org/ffmpeg/").

Good Luck!

---

### Post by Yellow Pasque on 2011-03-23
What format is your video in? Generally, you would demux the file (i.e. split it into audio and video), edit the audio, and mux the video and edited audio back together.

---

### Post by cchhrriiss121212 on 2011-03-23
Avidemux can do that with a few clicks, the technical terms are muxing (adding audio) and demuxing (removing audio).

---

### Post by shantiq on 2011-03-23
hi charlesh   if you turn your file into an mkv file with  ffmpeg



```
ffmpeg -i name.format(avi/mpg/flv/whatever it is)  -acodec copy -b 2000k (or whatever your video size is to start with)   name.mkv
```


you can then use mkvextract 

```
sudo apt-get install mkvtoolnix
```

 to separate audio from vid then edit audio in audacity as you suggest and stitch it back in say kdenlive (find it in synaptic)


```

[CODE]mkvmerge -i MovieFile.mkv

```You’ll see a listing similar to this:

File 'MovieFile.mkv': container: Matroska
Track ID 1: subtitles (S_TEXT/***)
Track ID 2: audio (A_MPEG/L3)
Track ID 3: video (V_MPEG4/ISO/AVC)
[B]Next, use mkvextract to extract certain tracks / attachments based on the output from the above command:
[/B]```

mkvextract tracks MovieFile.mkv 1:thesubtitles.srt
  2:theaudio.mp3 3:thevideo.mp4
```
[/CODE]


this is one route you can take:KS

---

### Post by cfhowlett on 2011-03-23
> **Temüjin said:**
> What format is your video in? Generally, you would demux the file (i.e. split it into audio and video), edit the audio, and mux the video and edited audio back together.

Files are .mp4.  

Would you please expound more on "demux", i.e. command line or via one of my applications?  Thanks.

---

### Post by Yellow Pasque on 2011-03-23
Install avidemux. Read wiki: [http://www.avidemux.org/admWiki/doku.php](http://www.avidemux.org/admWiki/doku.php)

---

### Post by howefield on 2011-03-24
Duplicate Threads merged.

---

### Post by FakeOutdoorsman on 2011-03-24
> **charlesh1609 said:**
> Greetings:

So I've recorded some video in the field, i.e. outside, windy, noisy, etc.  I would like to strip out the audio, clean it up in Audacity and then repatriate it back to the video.  Video is in .mp4 format.  HOW TO PROCEED?  

By the way, film makers should feel free to upgrade my vocabulary.  I'm sure there's an industry term for what I described, but I don't know what that might be.

Thanks in advance.

Step-by-step example time using FFmpeg:

1. Output a wav file for Audacity:
```
ffmpeg -i input.mp4 audio.wav
```

2. Clean *audio.wav* with Audacity.

3. Combine files. We will simply copy the video (no re-encoding so it's fast and looks good) and re-encode *audio.wav* all in one step. Actually, two steps because the first step will show you some info about the inputs:
```
ffmpeg -i input.mp4 -i audio.wav
```
FFmpeg barfs out a bunch of stuff. The important info:
```
    Stream #0.0: Video: h264 (High), yuv420p, 1280x720, PAR 115:87 DAR 1840:783, 23.98 fps, 24 tbr, 1k tbn, 47.95 tbc (default)
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16 (default)
...
    Stream #1.0: Audio: pcm_s16le, 22050 Hz, 2 channels, s16, 705 kb/s

```
So we now know video is *stream #0.0* and the audio you want is *stream #1.0*. Time to combine:
```
ffmpeg -i input.mp4 -i audio.wav -map 0:0 -map 1:0 -vcodec copy -acodec libfaac -ab 128k output.mp4
```

---

