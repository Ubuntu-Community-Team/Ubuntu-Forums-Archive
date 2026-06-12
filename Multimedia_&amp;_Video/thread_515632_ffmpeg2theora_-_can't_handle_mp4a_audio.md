---
title: "ffmpeg2theora - can't handle mp4a audio?"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by bpont on 2007-08-02
I'm trying to convert a .mov file with video and audio...the output file contains only video...here are the input specs:
```

  Duration: 00:05:44.8, start: 0.000000, bitrate: 311 kb/s
  Stream #0.0(eng): Audio: mp4a / 0x6134706D, 32000 Hz, stereo
  Stream #0.1(eng): Video: mpeg4, yuv420p, 320x240, 25.00 fps(r)
  Stream #0.2(eng): Data: rtp  / 0x20707472
  Stream #0.3(eng): Data: rtp  / 0x20707472
  Resize: 320x240
      0:05:44.80 audio: 0kbps video: 200kbps 
```

Is mp4a not supported?  Do I need an additional package or what?  Anyone know how to do this correctly? Thanks.

---

### Post by qyot27 on 2007-08-02
According to its changelog, it can do the conversion, although I'm not sure if it supports AAC in MOV, which is the particular issue here.  However, you might either have to transmux the original video from MOV to the MP4 container (which is the proper container the stream types you have should be in, even though from what I know MOV stores them correctly), or just convert the audio separately and use something like [OGMTools](http://www.bunkus.org/videotools/) to mux the audio and video together (personally, I'd not use the OGM container at all - MKV has pretty effectively taken its place; if this is for streaming, though, then whatever).

Mind if I ask why you need to do the conversion?  Transcoding from one lossy format to another isn't recommended, and that's what it'll be doing on both video and audio fronts.

---

### Post by bpont on 2007-08-02
Hmmm...OK, thanks for the tips, although, I'm pretty n00bish when it comes to video/audio editing, so not sure if I'll go through the trouble ot seperating the audio channel, converting it, then rejoining it to the video channel.  I'm not doing this conversion out of necessity, it was more of an experiment.  I'm also trying to decide what container format / codecs are best suited for archival storage, so I can click on a video file ten or twenty years from now and not worry about whether or not the video/audio will play correctly.  At the moment, I'm placing my bets on ogg theora...what do you think?  Thanks again.

---

### Post by qyot27 on 2007-08-02
Well, then I don't think that there'll be much of a problem the way it is (although like I said, it'd be better if it was in MP4 instead of MOV), seeing as how both the video and audio are MPEG standards, and MPEG-1 and MPEG-2 are still well supported now and they've been around for 12-15 years - MPEG-1 was ratified in 1991 or 1992, MPEG-2 a couple of years later.  As it stands, MPEG-4 has been around for almost 10 years already (having been ratified in 1998, and appended with the inclusion of H.264/AVC in 2003).

Also, I doubt that the libavcodec library (the core of VLC and mplayer, and ffdshow on Windows) will scale back its codec support for any of the MPEG formats for as long as it exists, seeing as [particularly MPEG-4] MPEG formats are one of the prime focuses for that project.  I generally do view MPEG formats as safe bets for hardware or software compatibility, although it does tread into the free/proprietary software divide sometimes and I know that purists may not want to touch them for that reason (just look at some of the controversy over MP3 decoders, and MP3 dates all the way back to MPEG-1).

Basically, due to the way viewer-ready (lossy) codecs work, recompressing them eventually leads to generational decay, much the same way making a copy of a copy of a copy of a copy of a VHS tape does.  If it's in terms of projects exported from an editing program (like Adobe Premiere, Avid, or Final Cut Pro - Cinelerra for the closest Linux solution), then it would be best to export in whichever lossless format is readily available and store that for archival purposes - that way you at least have the highest-quality master possible, although lossless codecs aren't meant for viewing.

---

### Post by kelvin spratt on 2007-08-02
Avidmux should do the job but not always in feisty certainly in Debian and every other OS,but give it a try you can just copy the vid change the sound, MOv and MP4 are very much alike mov being apple, DeVeDe also handles mov with no problem if you have a DVD writer, DVDs are as cheap as CDs where i live

---

### Post by bpont on 2007-08-02
qyot27, thanks for all the great advice.  Which lossless format do you recommend?  Which lossy codec do you like best?  Do you think ogg theora has a good future for lossy compression?  Thanks again for all the great info.

---

### Post by bpont on 2007-08-02
Kelvin, I tried using Avidemux on a .mov file but it didn't work correctly.  Basically, I just copied over the video and audio layers as is and transfered them into the mp4 container, but it made the audio speed up for some reason.  If you care to try it yourself, the file I used is at [this link]("http://www.megaupload.com/?d=Q1D6TY9R").  Thanks.

---

### Post by qyot27 on 2007-08-03
> **bpont said:**
> qyot27, thanks for all the great advice.  Which lossless format do you recommend?  Which lossy codec do you like best?  Do you think ogg theora has a good future for lossy compression?  Thanks again for all the great info.
Unfortunately this area is one that Linux isn't mature enough in yet for my tastes.  The two that I always rely on are HuffYUV (including the separate YV12-mode HuffYUV implementation in ffdshow's VFW) and Lagarith.  Both are, as far as I know, Windows-only, although you might have some luck making and decoding HuffYUV files with Avidemux, or via VirtualDubMod in Wine - also requires installing the codecs in Wine.  With AviSynth* 3.0 (which is still in very alpha stages) being cross-platform, there may very well be a strong demand to port both of them, though.  As for lossless audio, I can confidently recommend FLAC (and FLAC can be used in video files if you use MKV, at least).  Be aware, however, that lossless codecs eat up a lot of room, although still not as much as Uncompressed video or audio would.  Burning them off to DVD±R as data is a good solution.

*AviSynth is a powerful video processing script language - mostly used to do filtering transformations like smoothing, color adjustments, inverse telecine/deinterlacing, or resizing, but can also be used as a non-linear editor (but it doesn't have a GUI; there are a couple of projects working on that too, though - one is being primarily developed for OS X, the other more platform-independent from what I can gather)

As for lossy codecs, I've completely switched to H.264 (via x264) and AAC for distribution, although I do use XviD (an implementation of MPEG-4 Part 2 Advanced Simple Profile, although I doubt I actually needed to elaborate on that) and MP3 for test renders since my system is so old it has trouble not only decoding H.264, but also encoding it, especially with the settings I use.

I honestly don't know too much about Theora except that it's based on On2's VP3 format, and due to that has a pretty good chance of being used in a bevy of streaming applications.  I'm not sure which version of the VP series of codecs is used for videos uploaded to Youtube, but with the development behind Theora I'd assume it's at least on par with one of those (note: the amazing bad video quality on Youtube is determined by the restrictions they've placed on the encoding that happens there, not on the format itself).

EDIT: Seems YouTube doesn't use one of the VP codecs - it uses Sorenson Spark H.263 (of which I have absolutely no knowledge, although I assume it's roughly comparable to an unoptimized MPEG-4 Simple Profile such as what Quicktime 6 could spit out, with worse and more restrictive bitrate allocation).

For muxing the video and audio streams directly from MOV to MP4, I'd recommend using MP4Box.  You might have to specify the original framerate, though.  In the case of MKV - for future reference - then there's MKVToolNix, specifically mkvmerge (which does have an easy to use GUI).

---

