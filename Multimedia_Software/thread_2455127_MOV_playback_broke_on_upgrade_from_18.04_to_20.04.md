---
title: "MOV playback broke on upgrade from 18.04 to 20.04"
date: 2020-12-13
forum: Multimedia Software
---

### Post by computer_freak_8 on 2020-12-13
I've been using Ubuntu as my primary OS since 7.04, and haven't needed the forums for a while, but with this latest LTS upgrade, I ran into an issue I can't seem to fix. MOV playback for files from my dashcams broke. They still work fine everywhere else, including an older 18.04 installation I have, and a couple clean 20.04 installations I've tried. So it's something specific to this one installation where something broke, and I'm not sure where to start with troubleshooting (beyond what I've already done).
It should be noted that both VLC and Totem can play the audio - just not the video. VLC gives an error and Totem just gives a black screen. VLC's error is attached; it says:
```
Codec not supported:
VLC could not decode the format "h264" (H264 - MPEG-4 AVC (part 10))
```

**Codecs recommended from places all over the internet, but already installed:**
```
gstreamer1.0-libav is already the newest version (1.16.2-2).
gstreamer1.0-plugins-bad is already the newest version (1.16.2-2.1ubuntu1).
gstreamer1.0-plugins-ugly is already the newest version (1.16.2-2build1).
libdvdnav4 is already the newest version (6.0.1-1build1).
libdvdread7 is already the newest version (6.1.0+really6.0.2-1).
libdvd-pkg is already the newest version (1.4.2-1-1).
ubuntu-restricted-extras is already the newest version (67).
ffmpeg is already the newest version (7:4.2.4-1ubuntu0.1)
```

Any ideas on what might be missing or how to fix it are appreciated.

---

### Post by SeijiSensei on 2020-12-13
Try smplayer+mpv
```
sudo apt install smplayer mpv
```
SMPlayer is a GUI; mpv is the player engine. You can use just "mpv /path/to/video.mov" and see if it works.


Still I can't understand why VLC would say it can't decode the "h264" format. I just played a bit of an H.264-encoded video in VLC without issue.

---

### Post by computer_freak_8 on 2020-12-13
Here's what I've got with those:
MPV:
```
$ mpv 2020_1004_202311_005\ \(copy\).MOV 
mpv: error while loading shared libraries: /usr/lib/x86_64-linux-gnu/libOpenCL.so.1: file too short
```

SMPlayer
```
/usr/bin/mpv --no-config --no-quiet --terminal --no-msg-color --input-file=/dev/stdin --msg-level=ffmpeg/demuxer=error --no-fs --hwdec=no --sub-auto=fuzzy --no-input-default-bindings --input-x11-keyboard=no --no-input-cursor --cursor-autohide=no --no-keepaspect --wid=54525972 --monitorpixelaspect=1 --osd-level=1 --osd-scale=1 --sub-ass --embeddedfonts --ass-line-spacing=0 --sub-scale=1 --sub-text-shadow-color=#ff000000 --sub-codepage=ISO-8859-1 --sub-pos=100 --volume=55 --cache=auto --screenshot-template=cap_%F_%p_%02n --screenshot-format=jpg --softvol=yes --softvol-max=110 --term-playing-msg=MPV_VERSION=${=mpv-version:}
INFO_VIDEO_WIDTH=${=width}
INFO_VIDEO_HEIGHT=${=height}
INFO_VIDEO_ASPECT=${=video-params/aspect}
INFO_VIDEO_FPS=${=container-fps:${=fps}}
INFO_VIDEO_FORMAT=${=video-format}
INFO_VIDEO_CODEC=${=video-codec}
INFO_AUDIO_FORMAT=${=audio-codec-name}
INFO_AUDIO_CODEC=${=audio-codec}
INFO_AUDIO_RATE=${=audio-params/samplerate}
INFO_AUDIO_NCH=${=audio-params/channel-count}
INFO_LENGTH=${=duration:${=length}}
INFO_DEMUXER=${=current-demuxer:${=demuxer}}
INFO_SEEKABLE=${=seekable}
INFO_TITLES=${=disc-titles}
INFO_CHAPTERS=${=chapters}
INFO_TRACKS_COUNT=${=track-list/count}
METADATA_TITLE=${metadata/by-key/title:}
METADATA_ARTIST=${metadata/by-key/artist:}
METADATA_ALBUM=${metadata/by-key/album:}
METADATA_GENRE=${metadata/by-key/genre:}
METADATA_DATE=${metadata/by-key/date:}
METADATA_TRACK=${metadata/by-key/track:}
METADATA_COPYRIGHT=${metadata/by-key/copyright:}
INFO_MEDIA_TITLE=${=media-title:}
INFO_STREAM_PATH=${stream-path}
 --audio-client-name=SMPlayer --term-status-msg=STATUS: ${=time-pos} / ${=duration:${=length:0}} P: ${=pause} B: ${=paused-for-cache} I: ${=core-idle} VB: ${=video-bitrate:0} AB: ${=audio-bitrate:0} /home/jaredtbrees/sandbox/2020_1004_202311_005 (copy).MOV

/usr/bin/mpv: error while loading shared libraries: /usr/lib/x86_64-linux-gnu/libOpenCL.so.1: file too short

```

Audacity also won't launch with the same "file too short" error - it's a link that points to libOpenCL.so.1.0.0 which is a zero-byte file.

---

### Post by deadflowr on 2020-12-13
libOpenCL.so.1 (and libOpenCL.so.1.0.0)
are part of the ocl-icd-libopencl1 package.
You can try reinstalling that.
It shouldn't be a zero-byte file, it should be around 47Kb.

---

### Post by computer_freak_8 on 2020-12-13
> **deadflowr said:**
> libOpenCL.so.1 (and libOpenCL.so.1.0.0)
are part of the ocl-icd-libopencl1 package.
You can try reinstalling that.

Beautiful! Did an "apt purge" on it, which removed Gimp, Audacity, VLC, mpv, and a whole host of other stuff. Reinstalled Gimp, Audacity, VLC, and that re-installed ocl-icd-libopencl1 as a dependency. Now it all works again. Thanks so much!

---

### Post by CelticWarrior on 2020-12-13
You did it the hard & slow way.

It would have been much easier just reinstalling, as suggested.
```
sudo apt install --reinstall [COLOR=#000000]*ocl-icd-libopencl1*[/COLOR]
```

---

### Post by computer_freak_8 on 2020-12-19
> **CelticWarrior said:**
> You did it the hard & slow way.

True, but I don't mind missing the cruft; it removed a handful of packages I installed long ago that I never use anymore. I assume some cruft of some sort is what caused this in the first place; a purge is cleaner which was preferable for me in this case.

---

