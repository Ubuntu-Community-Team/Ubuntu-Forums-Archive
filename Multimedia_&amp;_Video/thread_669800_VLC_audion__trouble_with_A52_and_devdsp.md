---
title: "VLC audion  trouble with A52 and /dev/dsp"
date: 2008-01-16
forum: Multimedia &amp; Video
---

### Post by dplecto on 2008-01-16
I am using Ubuntu 7.10 and use VLC to play my video files.
       The video plays fine, but audio has some trouble.

When I play a divx file, both the video and audio is good , though  I get this print in terminal:
```

VLC media player 0.8.6c Janus
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
[00000347] oss audio output error: cannot open audio device (/dev/dsp)

```

/dev/dsp should have opened without any trouble since it's group (audio) has read write permissions and my user account is also under audio group (apart from its main group).

But since the audio playback is fine, it is not a problem.

The problem comes when i play avi files with a52 (AC-3) encoded audio. My comp has all the required codec (as far as my knowledge goes). But still i can't get any audio.  The message printed on the terminal is:
```

VLC media player 0.8.6c Janus
[00000343] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
```

          I can play the same video file in mplayer or anyother video player other then VLC.

        I had found a solution in this thread: [http://ubuntuforums.org/showthread.php?t=601522]("http://ubuntuforums.org/showthread.php?t=601522")
It recommends to  "_install libsdl1.2debian-all_ " but, I cannot remove pulse since it is required for Amarok, Xine, mplayer a whole lot of other stuff. 

Is there a solution for this ?

---

