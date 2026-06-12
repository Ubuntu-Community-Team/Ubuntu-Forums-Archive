---
title: "Sound goes mute after some minutes of playback"
date: 2016-05-10
forum: Multimedia Software
---

### Post by linuxyogi on 2016-05-10
Hi, 
I am using Ubuntu 16.04. Problem is when I boot the system and play any video file I hear audio as usual but after some minutes of playback it goes mute. I checked the audio setting in the tray but cant find anything wrong there.
This is a 1 day old installation. 

Please help me out.

Edit : pulseaudio -k  brings back the sound but this cant be a permanent solution.

---

### Post by vasa1 on 2016-05-11
Please see #14 in [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"): >     Bumping your thread if you receive no answer is acceptable. Premature and excessive bumping could attract staff attention and action. If you wish to bump, consider time zones - the one with your answer might be asleep. Bumping your post means it will not appear in the unanswered posts search and will escape the notice of the Unanswered Posts Team.

---

### Post by QIII on 2016-05-11
We consider about 12 hours to be an appropriate amount of time to wait before bumping.  That will give your request exposure on the other side of the globe.

Cheers!

---

### Post by linuxyogi on 2016-09-02
Here's my mpv log

```
/usr/bin/mpv --no-config --no-quiet --terminal --no-msg-color  --input-file=/dev/stdin --no-fs --hwdec=no --sub-auto=fuzzy --vo=xv  --ao=pulse --no-input-default-bindings --input-x11-keyboard=no  --no-input-cursor --cursor-autohide=no --no-keepaspect --wid=14680081  --monitorpixelaspect=1 --osd-scale=1 --sub-ass --embeddedfonts  --ass-line-spacing=0 --sub-scale=1 --sub-text-font=Arial  --sub-text-color=#ffffff --sub-text-shadow-color=#000000  --sub-text-border-color=#000000 --sub-text-border-size=2.5  --sub-text-shadow-offset=5 --sub-codepage=utf8:ISO-8859-1 --vid=1  --aid=1 --sub-pos=100 --volume=110 --cache=2048 --osd-level=0  --screenshot-directory=/home/mint/Pictures/smplayer_screenshots  --screenshot-template=cap_%F_%p_%02n --screenshot-format=jpg  --audio-channels=2 --af-add=scaletempo  --af-add=equalizer=0:0:0:0:0:0:0:0:0:0 --softvol=yes --softvol-max=110  --ytdl=no --term-playing-msg=MPV_VERSION=${=mpv-version:}
INFO_VIDEO_WIDTH=${=width}
INFO_VIDEO_HEIGHT=${=height}
INFO_VIDEO_ASPECT=${=video-aspect}
INFO_VIDEO_FPS=${=fps}
INFO_VIDEO_FORMAT=${=video-format}
INFO_VIDEO_CODEC=${=video-codec}
INFO_AUDIO_FORMAT=${=audio-codec-name:${=audio-format}}
INFO_AUDIO_CODEC=${=audio-codec}
INFO_AUDIO_RATE=${=audio-params/samplerate:${=audio-samplerate}}
INFO_AUDIO_NCH=${=audio-params/channel-count:${=audio-channels}}
INFO_LENGTH=${=duration:${=length}}
INFO_DEMUXER=${=demuxer}
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
 --term-status-msg=STATUS:  ${=time-pos} / ${=duration:${=length:0}} P: ${=pause} B:  ${=paused-for-cache} I: ${=core-idle} /home/mint/input.mp4

Playing: /home/mint/input.mp4
 (+) Video --vid=1 (*) (h264)
 (+) Audio --aid=1 --alang=und (*) (aac)
AO: [pulse] 44100Hz stereo 2ch float
VO: [xv] 1280x720 yuv420p
[vo/xv/x11] Disabling screensaver failed (4). Make sure the xdg-screensaver script is installed.
INFO_VIDEO_DSIZE=1280x720
MPV_VERSION=mpv 0.14.0
INFO_VIDEO_WIDTH=1280
INFO_VIDEO_HEIGHT=720
INFO_VIDEO_ASPECT=1.777778
INFO_VIDEO_FPS=25.000000
INFO_VIDEO_FORMAT=h264
INFO_VIDEO_CODEC=H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 [lavc:h264]
INFO_AUDIO_FORMAT=aac
INFO_AUDIO_CODEC=AAC (Advanced Audio Coding) [lavc:aac]
INFO_AUDIO_RATE=44100
INFO_AUDIO_NCH=2
INFO_LENGTH=264.218333
INFO_DEMUXER=lavf
INFO_TITLES=
INFO_CHAPTERS=0
INFO_TRACKS_COUNT=2
METADATA_TITLE=
METADATA_ARTIST=
METADATA_ALBUM=
METADATA_GENRE=
METADATA_DATE=
METADATA_TRACK=
METADATA_COPYRIGHT=
INFO_MEDIA_TITLE=input.mp4
INFO_TRACK_0: video 1 'und' '' yes
INFO_TRACK_1: audio 1 'und' '' yes
[ao/pulse] pa_stream_cork() failed: Connection terminated
[ao/pulse] pa_stream_flush() failed: Connection terminated
[ao/pulse] pa_stream_cork() failed: Connection terminated
[ao/pulse] pa_stream_cork() failed: Connection terminated
[ao/pulse] pa_stream_flush() failed: Connection terminated
[ao/pulse] pa_stream_cork() failed: Connection terminated
AO: [pulse] 44100Hz stereo 2ch float
INFO_VIDEO_BITRATE=1312780
INFO_AUDIO_BITRATE=193109
```

---

