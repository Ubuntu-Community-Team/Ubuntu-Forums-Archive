---
title: "FFMPEG/Python stream from webcam"
date: 2011-10-04
forum: Multimedia Software
---

### Post by jeebusman on 2011-10-04
Hey guys,

When I run the following command from terminal, FFMPEG is able to record a video/audio stream from my webcam and mic perfectly without any issues.

```

ffmpeg -f alsa -i default -itsoffset 00:00:00 -f video4linux2 -s 1280x720 -r 25 -i /dev/video0 out.avi

```

When I try and execute the same command from within this Python script:

```

def call_command(command):
    subprocess.Popen(command.split(' '))

call_command("ffmpeg -f alsa -i default -itsoffset 00:00:00 -f video4linux2 -s 1280x720 -r 25 -i /dev/video0 out.avi")

```

I get the following error:

```

Input #0, alsa, from 'default':
  Duration: N/A, start: 1317762562.695397, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, 1 channels, s16, 705 kb/s
[video4linux2 @ 0x165eb10]Cannot find a proper format for codec_id 0, pix_fmt -1.
/dev/video0: Input/output error

```

Could anyone shed some light on what could be going on here? I've tried using os.system() as well as subprocess.call() and it gives me the same errors. I'm not sure where to start on what could be going wrong here. I tried searching for the v4l2 error, but couldn't find anything consistent.

---

