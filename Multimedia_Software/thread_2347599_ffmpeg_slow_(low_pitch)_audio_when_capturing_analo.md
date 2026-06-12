---
title: "ffmpeg slow (low pitch) audio when capturing analog-stereo.monitor"
date: 2016-12-27
forum: Multimedia Software
---

### Post by webmqster on 2016-12-27
Since a few months I have a strange problem when recording with ffmpeg, where the audio is too slow and in lower pitch than the original.

I  first encountered the issue using kazam, so I tried OBS with the same results.

So, I tried reproducing the issue using the CLI via the terminal.

This command captured the microphone and produced a video with perfect speed (normal pitch) audio:
```
ffmpeg -y -f pulse -i default -r 30 -f x11grab -s 1920x1080 -i ${DISPLAY} -c:v libx264rgb -crf 0 -preset:v ultrafast -c:a pcm_s16le -af aresample=async=1:first_pts=0 out1.mkv
```

This command captured the analog-audio.monitor and produced a video with too slow (low pitch) audio that skips every now and then to catch up with the video:
```
ffmpeg -y -f pulse -i alsa_output.pci-0000_00_14.2.analog-stereo.monitor -r 30 -f x11grab -s 1920x1080 -i ${DISPLAY} -c:v libx264rgb -crf 0 -preset:v ultrafast -c:a pcm_s16le -af aresample=async=1:first_pts=0 out2.mkv
```

The issue seems to be tied and limited to using ffmpeg with the audio source being the analog audio monitor.

In case you want to try and reproduce the issue, I got the 'monitor' using this command:
```
pactl list sources | grep analog-stereo.monitor
```

I am using Ubuntu 14.04.

ffmpeg -version returns this:
```

ffmpeg version 3.2.2 Copyright (c) 2000-2016 the FFmpeg developers
built with gcc 4.8 (Ubuntu 4.8.4-2ubuntu1~14.04.3)
configuration: --extra-libs=-ldl --prefix=/opt/ffmpeg --mandir=/usr/share/man --enable-avresample --disable-debug --enable-nonfree --enable-gpl --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --disable-decoder=amrnb --disable-decoder=amrwb --enable-libpulse --enable-libfreetype --enable-gnutls --enable-libx264 --enable-libx265 --enable-libfdk-aac --enable-libvorbis --enable-libmp3lame --enable-libopus --enable-libvpx --enable-libspeex --enable-libass --enable-avisynth --enable-libsoxr --enable-libxvid --enable-libvidstab --enable-libwavpack --enable-nvenc
libavutil      55. 34.100 / 55. 34.100
libavcodec     57. 64.101 / 57. 64.101
libavformat    57. 56.100 / 57. 56.100
libavdevice    57.  1.100 / 57.  1.100
libavfilter     6. 65.100 /  6. 65.100
libavresample   3.  1.  0 /  3.  1.  0
libswscale      4.  2.100 /  4.  2.100
libswresample   2.  3.100 /  2.  3.100
libpostproc    54.  1.100 / 54.  1.100
```

Anyone got a clue what is going on and how to fix this?

---

### Post by webmqster on 2016-12-27
I finally found the cause of this issue.

Apparently pulseaudio doesn't know what it wants. It tells everyone it's using 48khz when it's really using 44.1khz.

The fix:

Uncomment default-sample-rate = 44100 in /etc/pulse/daemon.conf and set it to 48000

source: [http://superuser.com/questions/691126/avconv-recording-pulseaudio-output-monitor-stretches-audio](http://superuser.com/questions/691126/avconv-recording-pulseaudio-output-monitor-stretches-audio)

---

