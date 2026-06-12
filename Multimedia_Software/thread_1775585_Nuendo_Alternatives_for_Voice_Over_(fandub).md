---
title: "Nuendo Alternatives for Voice Over (fandub)?"
date: 2011-06-04
forum: Multimedia Software
---

### Post by rosenkavalier on 2011-06-04
[FONT="Comic Sans MS"][COLOR="Blue"]Hello...

I want to do some amateur voice over works. I need an audio editor that can also play the video simultaneously to sync with the character's lip movements.

The problem is my video sources are in h264 mkv, I guess it is not very friendly with many softwares.

Here's what I've searched (tried some of them too) and the results:

[LIST]
[*]LiVES -> can't compile with kernel 2.6.38, the offered patch (in sf) rejected (maybe different source file from the one specified in the patch)
[*]Cinerella, can't accept mkv or mp4. (after that I tried to get the source video loaded to Cinerella)
[*]x264, transcoding to lower the resolution -> no avi container output, sync problem with raw h264 stream output
[*]avidemux_qt, trying to mux the transcoded video to avi -> crashed with h264 input video, either in elementary stream or matroska format (I doubt Cinerella will accept avi videos with h264 codec, if I could ever make one)
[*]ffmpeg, transcode from h264 to xvid -> shared library error: libavutil.so.49 not found
[*]xvidenc shell script -> no mencoder (I'm using mplayer2)
[/LIST]

any help will be appreciated ;)

if I can't find other way around, guess I'll go with the fallback: rolling armed track in audacity while playing the video, no fine control over the recorded track but I can edit it later...[/COLOR][/FONT]

---

### Post by rosenkavalier on 2011-06-07
bump

---

