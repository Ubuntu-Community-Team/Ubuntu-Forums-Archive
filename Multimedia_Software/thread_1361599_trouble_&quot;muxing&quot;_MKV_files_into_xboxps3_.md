---
title: "trouble &quot;muxing&quot; MKV files into xbox/ps3 readible files"
date: 2009-12-22
forum: Multimedia Software
---

### Post by eival on 2009-12-22
im using advidemux which for the most part has a great default option when you open it to "copy" the audio and video of any container into MP4 or AVI an it only takes 1-2 seconds, the only problem is, sometimes the audio doesnt play on the "mux'ed" version, or the xbox/ps3 will say its an incompatible format.

seeing as how most of these MKV files are bluray rips which range atleast 3 to 4 gigs and up, doing a standard convert isnt an option.

i heard the PS3 can play more varieties of containers and formats than the XBOX, like VOB, but advidimux only lets me use MP4 or AVI, so is there is any other Ubuntu app that can "mux" MKV into any PS3/360 compatible container/format?

---

### Post by lovinglinux on 2009-12-22
Avidemux doesn't handle h264 very well. [Mencoder](apt:mencoder) is the best IMO for such conversions. See commands and examples [here](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html#GENERAL%20ENCODING%20OPTIONS%20%28MENCODER%20ONLY%29).

---

### Post by VertexPusher on 2009-12-22
> **eival said:**
> im using advidemux which for the most part has a great default option when you open it to "copy" the audio and video of any container into MP4 or AVI an it only takes 1-2 seconds, the only problem is, sometimes the audio doesnt play on the "mux'ed" version, or the xbox/ps3 will say its an incompatible format.
Both XBox and PS3 impose format restrictions that you need to respect if you want to make files play back properly on those devices. Simply choosing "Copy" mode in Avidemux does not always work.

For example, many MKVs come with AC-3 or Vorbis audio streams. While Avidemux may be able to copy these streams to an MP4 container, XBox and PS3 can't play them back. You must convert the audio to AAC.

There's a similar problem with video. For example, the PS3 can play back DivX 5/6 files, but not MPEG-4 ASP content in MP4 containers. H.264 may or may not work, depending on the settings used to encode the video. In some cases you may need to re-encode anyway because B-Pyramid or other H.264 High Profile features were used which are not supported in XBox and PS3.

Switching the tool will not make these problems go away. You can't just streamcopy stuff into MP4 or AVI and expect it to work anywhere. You can try, but if it doesn't work, you'll have to re-encode, no matter which tool you are using.

---

### Post by beegary on 2009-12-22
>  
You can try, but if it doesn't work, you'll have to re-encode, no matter which tool you are using.

what tool/command do you use to re-encode? are there any guides, specifically for re-encoding for PS3 playback? Im missing erightsoft SUPER!!!!

---

### Post by VertexPusher on 2009-12-22
> **beegary said:**
> what tool/command do you use to re-encode?
Avidemux. I encoded videos for a fansub group for a while, and Avidemux is the only encoder on Linux featuring a working SSA subtitles renderer. We released our files in DivX Plus format but made sure that they could be streamcopied to MP4 for PS3 playback. DivX Plus is H.264 (High Profile Level 4.0, max. 3 B-frames) and AAC (Low Complexity Profile) in MKV.

> are there any guides, specifically for re-encoding for PS3 playback?
I could list the settings we used, but it's probably easier for you to check out the avidemux.org forums for PS3 presets that you can import and access through the menu.

---

