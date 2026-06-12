---
title: "PulseAudio configuration in 5.1 environment"
date: 2008-11-08
forum: Multimedia Software
---

### Post by 0x656b694d on 2008-11-08
Hi,

I've got SBLive! 5.1 sound card + 5.1 speaker environment here.

What is alright:
[LIST]
[*]I can control each of six speakers via PulseAudio mixer
[*]Stereo is upmixed to 6 speakers
[/LIST]

What i did over standard installation:
[LIST=1]
[*]/etc/pulse/daemon.conf: default-sample-rate = 48000, default-sample-channels = 6
[*]ALSA mixer has the following settings:
[list]
[*]Surround: 50%
[*]3D Control: off
[*]Sigmatel 4-Speaker Stereo: off
[/list]
[/LIST]

Current problems are:
[LIST=1]
[*]pulseaudio process takes 20-50% of CPU, sometimes with peaks up to 100% &#8212; one per 5 seconds. What is it doing? Upmixing? Resampling? May it use hardware surround?
[*]Sound is superimposed: if ALSA Master or PCM channel is on, i hear Stereo+Upmix=Surround, if i mute the Master or PCM, i still hear something which is Surround&#8722;Stereo=Upmix, i.e. surround minus front channels. How do i mute everything i hear by a click?
[/LIST]

Thanks in advance!!
-Mike

---

### Post by 0x656b694d on 2008-11-08
Wow,
**W: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.**
*Soft CPU time limit exhausted, terminating.* &#8592; Must be fixed in PA 9.12.
Why??
```

$ pulseaudio 
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SAA7134.pcm.surround51.0:CARD=1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM surround51:1
ALSA lib conf.c:3952:(snd_config_expand) Unknown parameters 1
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM surround71:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SAA7134.pcm.surround51.0:CARD=1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM surround50:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SAA7134.pcm.surround51.0:CARD=1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM surround41:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SAA7134.pcm.surround40.0:CARD=1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM surround40:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SAA7134.pcm.front.0:CARD=1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM front:1
W: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
W: alsa-util.c: Cannot find fallback mixer control "Mic".
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL surround51:0
ALSA lib conf.c:3952:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM surround71:0
ALSA lib setup.c:96:(snd_sctl_install) Cannot lock ctl elem
**W: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.**
**Soft CPU time limit exhausted, terminating.**

```

---

### Post by 0x656b694d on 2008-11-09
Oh, okay.

That all pulseaudio stuff just doesn't work.

Will wait for fixes, and hope.

---

