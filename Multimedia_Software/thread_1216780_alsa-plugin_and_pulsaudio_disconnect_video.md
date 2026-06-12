---
title: "alsa-plugin and pulsaudio disconnect video"
date: 2009-07-18
forum: Multimedia Software
---

### Post by mps_1 on 2009-07-18
Dear all

I have thoroughly searched the forums but didn't found a solution to the following problem with the audio of video.

My system: compaq CQ40 with Ubuntu 9.04-Jaunty. I use **pulseaudio** for video and music (I followed the instructions from *_[COLOR="Plum"]http://ubuntuforums.org/showthread.php?t=1130384[/COLOR]_* to configure sound and it worked fine for some months until now, July 2009) 

Unexpectedly one day Totem begun to clash after some 25 seconds of reproducing any avi file (This did not happen with flash files). The same was observed with VLC, gxine and Media Player. Only Dragon Player worked fine. With the music, everything was OK. I think the problem was related to the my recent installation of virtualbox. I uninstall VB and reinstalled padevchooser, VLC, etc. and the problem remained. Inspecting Volume Control of Pulseaudio I realized that Totem and VLC use** ALSA-plugin**, but Dragon Player don't. I have the lattest versions of padevchooser and alsa.

**After clashing, the output from VLC is:**
> 00000476] alsa audio output error: cannot recover from buffer underrun
[00000476] alsa audio output error: ALSA error: Error de entrada/salida
vlc: pcm_pulse.c:312: pulse_delay: Afirmación `pcm->stream' fallida. ("failed" in spanish)

**With Totem, the message is: **
> ** Message: Error: Disconnected: Conexión terminada
pulsesink.c(451): gst_pulsesink_is_dead (): /GstPlayBin: play/GstBin:abin/GstBin:audiosinkbin/GstGConfAudioSink:audio-sink/GstBin:bin5/GstPulseSink: pulsesink1

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.


As I said before, I did not found a solution, except for using OSS for music and video. With this, totem worked fine but VLC don't.

Thanks for your attention and your help.```
[CODE]
```[/CODE]

---

### Post by igorzwx on 2009-07-18
install another Ubuntu in dual boot and try this:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

---

### Post by mps_1 on 2009-07-18
Thanks igorzwx

your replay was so quick that I didn't had time to tide up my message. I'll try your recommendation and post the result.

Cheers

---

