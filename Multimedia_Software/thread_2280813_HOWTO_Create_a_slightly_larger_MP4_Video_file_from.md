---
title: "HOWTO Create a slightly larger MP4 Video file from your MP3 Audio"
date: 2015-06-02
forum: Multimedia Software
---

### Post by rmstock2 on 2015-06-02
HOWTO Create a slightly larger MP4 Video file from your MP3 Audio
-----------------------------------------------------------------

Create a picture in PNG format. As picture size use either
480x360, 640x480 or other common used Video frame size formats.
Next create a MP4 Video from the MP3 Audio :

```

ffmpeg -qscale 2 -loop_input \
        -i radio-logo.png \
        -i radio-audio.mp3 \
        -shortest \
        -acodec libmp3lame -ar 44100 -ab 128k -aq 0 \
        radio-show.mp4

```

This will create a rather large file when using long mp3's of 1.5 to
2.5 hours length. (For a 1h45min mp3 and a 640x480 png image you will
go well beyond 1 Gbyte in video size). Next load radio-show.mp4 into
avidemux, where for Video choose MPEG-4 ASP (Xvid) and keep the
defaults, for Audio choose MP3 (lame) and select the same Bitrate as
inside the ffmpeg command : 128. Select as Format MP4

---

### Post by FakeOutdoorsman on 2015-06-03
Some comments about your command:

[list]
[*]*-qscale* is an output option, not an input option
[*]*-loop_input* is really old syntax (are you using an ancient build?). The recommended option is "-loop 1".
[*]Declaring *-ar* is likely unnecessary.
[*]*-ab* and *-aq* are mutually exclusive, so you should use only one. The *-aq* (or the alias *-q:a*) values change depending on the encoder. See the [docs](https://ffmpeg.org/ffmpeg-codecs.html) and [wiki](http://trac.ffmpeg.org/#CommunityContributedDocumentation) for info.
[*]MP3 in MP4 may not work in all players, such as WMP with certain audio sample rates...if I recall correctly. AAC audio is the norm for MP4.
[/list]

Creating a video then re-encoding it is an unnecessary step. You could just use one ffmpeg command instead of also using Avidemux:
```
ffmpeg -loop 1 -framerate 2 -i logo.png -i audio.mp3 -c:v libx264 -crf 23 -preset slow -tune stillimage -pix_fmt yuv420p -c:a copy -shortest output.mkv
```

[list]
[*]This command will use a lower frame rate for the image since you don't really need to use the default of 25.
[*]The audio is [stream copied](https://ffmpeg.org/ffmpeg.html#Stream-copy) so it isn't re-encoded.
[*]See [FFmpeg Wiki: H.264 Encoding Guide](https://trac.ffmpeg.org/wiki/Encode/H.264) for more info on *-crf*, *-preset*, and *-tune*.
[*]*-pix_fmt yuv420p* is added to ensure a compatible chroma subsampling scheme for non-FFmpeg based players (not necessary if uploading to YouTube).
[*]Matroska container is used because it can accept just about any audio format.
[/list]

If you need MP4 container:
```
ffmpeg -loop 1 -framerate 2 -i logo.png -i audio.mp3 -c:v libx264 -crf 23 -preset slow -tune stillimage -pix_fmt yuv420p -c:a aac -strict experimental -movflags +faststart -shortest output.mp4
```

If the video is being watched via progressive download, such as in a browser, then *-movflags +faststart* will allow playback to begin before the files is completely downloaded.

---

