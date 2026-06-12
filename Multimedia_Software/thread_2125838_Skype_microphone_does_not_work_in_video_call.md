---
title: "Skype microphone does not work in video call"
date: 2013-03-15
forum: Multimedia Software
---

### Post by michaelAust on 2013-03-15
I am using a Logitech QuickCam Communicate STX (046d:08d7), Lubuntu 12.10, and Skype 4.1.0.20.0-0ubuntu0.12.04.2 from the partner repos. With this camera in previous versions of linux I used to have to start skype version 2 with a "LD_PRELOAD ...v4l1compat.so skype" command to get video to work, but now I dont need to, as the setup works ok. Sound and video work ok in the setup interface and sound works fine in the test call, but when I do a video call the video works ok, but the other party cannot hear my sound. When I run it from the terminal there are lots of errors such as 
```
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

```
(Many consecutive duplicate lines removed to save space)
Many of these errors relate to PulseAudio, which is not installed in Lubuntu, so they don't make much sense to me.

---

