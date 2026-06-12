---
title: "Controlling a media server from another computer"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by James79 on 2007-07-18
My setup:

Computer A: Windows XP
Computer B: Linux MythTV/media pc

What I would like to do is control the music that's being played on B *from A*. The music needs to be played and output on B.

I would like to do this without using VNC, as B is often being used for other purposes.

The solution it seems to me was described [in this thread]("http://ubuntuforums.org/showthread.php?t=223907&highlight=playing+music+on+server"). So I installed Xming on A, and putty. I ssh into B with X forwarding enabled. So far so good, I can in fact run simple X apps such as gedit and xclock on my windows workstation.

The problem is with any app that attempts to open the sound device.As an example, here's the output I get from ssh when I try to play a file using vlc (I get the same errors with rhtyhmbox):

```

[jim@zebes ~]$ vlc
VLC media player 0.8.6c Janus

** (.:3100): CRITICAL **: clearlooks_style_draw_focus: assertion `height >= -1' failed

** (.:3100): CRITICAL **: clearlooks_style_draw_focus: assertion `height >= -1' failed
ALSA lib confmisc.c:848:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:397:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1248:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3972:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
JACK tmpdir identified as [/dev/shm]
[00000354] jack audio output error: failed to connect to JACK server
[00000354] oss audio output error: cannot open audio device (/dev/dsp)
ALSA lib confmisc.c:848:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:397:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1248:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3972:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:848:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:397:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1248:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3972:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
[00000354] esd audio output error: cannot open esound socket (format 0x00001021 at 44100 Hz)
[00000354] arts audio output error: arts_init failed (can't connect to aRts soundserver)
ALSA lib confmisc.c:848:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:397:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1248:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3972:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default


```

The poster from the other thread made it sound like it would "just work"... so I'm curious as to what I could be missing here. It seems to me that vlc is trying to open the audio device on my windows machine, which isn't what I want to do at all.

Any insight is greatly appreciated! Thanks!

---

### Post by James79 on 2007-07-19
Solved it! - the user I was logged in with did not have write permissions to /dev/dsp. chmod 666 later and we have audio :) 

I'm still getting the ALSA related errors however, although it appears that vlc is simply finding another way to do it's thing. 

Hope this can save others from the troubles I had.

---

### Post by Persianelfster on 2007-07-23
you downloaded ssh-server package right?

---

