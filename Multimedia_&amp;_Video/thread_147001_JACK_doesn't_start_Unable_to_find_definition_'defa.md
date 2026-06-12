---
title: "JACK doesn't start: Unable to find definition 'defaults.pcm.subdevice'"
date: 2006-03-19
forum: Multimedia &amp; Video
---

### Post by dolson on 2006-03-19
When I start JACK now on my Dapper system, it doesn't start properly. I get this:

```
creating alsa driver ... hw:0,0|hw:0,2|128|2|48000|0|0|nomon|swmeter|-|16bit
control device hw:0
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.pcm.subdevice'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2099:(snd_pcm_open_noupdate) Unknown PCM hw:0,0
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.pcm.subdevice'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2099:(snd_pcm_open_noupdate) Unknown PCM hw:0,2
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
```

I suspect it has to do with the fact that at one time, I had a USB MIDI keyboard plugged in, but uh, I haven't had it plugged into this PC for several days.

I am still new to JACK, so any help is appreciated.

---

### Post by Harry_Sack on 2006-03-19
I'm having this problem too.
Also after fiddling with my m-audio ozone, which is a soundcard/midikeyboard.

```
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:1,0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:1
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.pcm.subdevice'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2099:(snd_pcm_open_noupdate) Unknown PCM hw:1,0
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.pcm.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2099:(snd_pcm_open_noupdate) Unknown PCM hw:0
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
```

It works in DeMuDi 1.3.0.

New to Jack too, and also a linux newbie, so I don't really know how to fix this kind of problem.

Also, nice to see this project started. I want to use linux.

---

### Post by dolson on 2006-03-19
I think something has changed in Dapper recently that screwed this up... Because I was using it fine for the longest time in Breezy and earlier in Dapper... Just to track it down now.

There's already a bug opened in Malone for it, I just checked:

[https://launchpad.net/distros/ubuntu/+source/jack-audio-connection-kit/+bug/33903/](https://launchpad.net/distros/ubuntu/+source/jack-audio-connection-kit/+bug/33903/)

Let's hope someone who knows what they're doing will fix it...

---

### Post by dolson on 2006-03-22
Solved this issue as reported in the bug report by someone else.

rm ~/.asoundrc*

You could mv to /tmp if you want. If you didn't make changes to these files, then you have likely got nothing to worry about. I just deleted them and now JACK is working again. :D

---

### Post by bwanab on 2006-03-22
Does this problem have anything to do with the recent new kernel (2.6.15-19...)? I upgraded to this and on startup jack started reporting about 10 xruns per second even with no applications running. I rebooted back into 2.6.16-18 and it all works fine.

---

### Post by Harry_Sack on 2006-03-26
[QUOTE=dolson]Solved this issue as reported in the bug report by someone else.

rm ~/.asoundrc*

You could mv to /tmp if you want. If you didn't make changes to these files, then you have likely got nothing to worry about. I just deleted them and now JACK is working again. :D[/QUOTE]

Thanks.

---

