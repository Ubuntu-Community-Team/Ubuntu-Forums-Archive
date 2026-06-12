---
title: "No sound in 10.04"
date: 2010-05-16
forum: Multimedia Software
---

### Post by sloom22 on 2010-05-16
After upgrading from Ubuntu 9.10 to 10.04, sound stopped working on my Lenovo G530 laptop. Here are some diagnostics I ran. Any ideas how to fix it?
```

me@computer:~$ aplay -l
aplay: device_list:223: no soundcards found...

me@computer:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

me@computer:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Intel G45 DEVCTG

==> /proc/asound/card0/codec#2 <==
Codec: Conexant CX20561 (Hermosa)

me@computer:~$ mplayer file.mp3 
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing file.mp3.
Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
waitpid(): No child processes
AO: [pulse] Init failed: Internal error
Failed to initialize audio driver 'pulse'
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
[AO_ALSA] alsa-lib: conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
[AO_ALSA] alsa-lib: conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA] alsa-lib: conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA] alsa-lib: conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
[AO_ALSA] Playback open error: No such file or directory
Failed to initialize audio driver 'alsa'
[AO SDL] Samplerate: 44100Hz Channels: Stereo Format s16le
[AO SDL] using aalib audio driver.
[AO SDL] Unable to open audio: No available audio device
Failed to initialize audio driver 'sdl:aalib'
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video


Exiting... (End of file)
```

---

### Post by lidex on 2010-05-16
Use the alsa-upgrade link in my sig to upgrade alsa. Let me know how it goes.

---

### Post by sloom22 on 2010-05-18
Interestingly enough, after (IIRC) removing my ~/.pulse directory, and restarting pulse, and rebooting about twice - sound started working. It's sort of mysterious but I'm not complaining.

---

