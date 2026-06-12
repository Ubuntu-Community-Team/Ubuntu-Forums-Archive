---
title: "Jack not working after upgrade to Gusty"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by homerj742 on 2007-10-23
I was hoping somebody could help me out with this. Jack was working great under Fiesty, but after this upgrade I'm starting to get this error. I have 2 sound cards (one built in, and one M-Audio Delta 44). Please help! Thank you in advance:


I'm getting this error "Could not connect Jack server to client" 

and this in the messages

```







21:10:29.760 Patchbay deactivated.
21:10:29.928 Statistics reset.
21:10:30.011 Startup script...
21:10:30.011 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
JACK tmpdir identified as [/dev/shm]
21:10:30.076 MIDI connection graph change.
21:10:30.319 Startup script terminated with exit status=256.
21:10:30.324 JACK is starting...
21:10:30.325 /usr/bin/jackd -dalsa -dhw:1 -r44100 -p1024 -n2 -m
21:10:30.334 JACK was started with PID=20452 (0x4fe4).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:1|hw:1|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.namehint.extended'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM hw:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.namehint.extended'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM hw:1
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
21:10:30.391 JACK was stopped successfully.
21:10:30.392 Post-shutdown script...
21:10:30.393 killall jackd
jackd: no process killed
21:10:30.536 MIDI connection change.
21:10:30.617 Post-shutdown script terminated with exit status=256.
21:10:32.578 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
21:11:27.471 Startup script...
21:11:27.473 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
21:11:27.724 Startup script terminated with exit status=256.
21:11:27.725 JACK is starting...
21:11:27.727 /usr/bin/jackd -dalsa -dhw:1 -r96000 -p1024 -n2 -m
21:11:27.734 JACK was started with PID=20461 (0x4fed).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 96000
creating alsa driver ... hw:1|hw:1|1024|2|96000|0|0|nomon|swmeter|-|32bit
control device hw:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.namehint.extended'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM hw:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.namehint.extended'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM hw:1
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
21:11:27.809 JACK was stopped successfully.
21:11:27.811 Post-shutdown script...
21:11:27.812 killall jackd
jackd: no process killed
21:11:28.028 Post-shutdown script terminated with exit status=256.
21:11:29.789 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
21:11:55.304 Startup script...
21:11:55.306 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
21:11:55.560 Startup script terminated with exit status=256.
21:11:55.561 JACK is starting...
21:11:55.563 /usr/bin/jackd -dalsa -dhw:1 -r96000 -p1024 -n2 -m
21:11:55.570 JACK was started with PID=20468 (0x4ff4).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 96000
creating alsa driver ... hw:1|hw:1|1024|2|96000|0|0|nomon|swmeter|-|32bit
control device hw:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.namehint.extended'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM hw:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.namehint.extended'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM hw:1
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
21:11:55.604 JACK was stopped successfully.
21:11:55.605 Post-shutdown script...
21:11:55.605 killall jackd
jackd: no process killed
21:11:55.830 Post-shutdown script terminated with exit status=256.
21:11:57.702 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
21:12:09.379 Statistics reset.
21:12:10.563 Statistics reset.
21:12:30.418 Startup script...
21:12:30.418 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
21:12:30.663 Startup script terminated with exit status=256.
21:12:30.663 JACK is starting...
21:12:30.663 /usr/bin/jackd -dalsa -dhw:1 -r96000 -p1024 -n2 -m
21:12:30.676 JACK was started with PID=20475 (0x4ffb).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 96000
creating alsa driver ... hw:1|hw:1|1024|2|96000|0|0|nomon|swmeter|-|32bit
control device hw:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.namehint.extended'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM hw:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.namehint.extended'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM hw:1
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
21:12:30.683 JACK was stopped successfully.
21:12:30.684 Post-shutdown script...
21:12:30.684 killall jackd
jackd: no process killed
21:12:30.898 Post-shutdown script terminated with exit status=256.
21:12:32.844 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
```

---

### Post by Selbstmord on 2007-12-09
I have the same problem. I'm desperately trying to get recording to work with my IK Multimedia Stealthplug (Ardour2/JACK)...

Anyone know what's up?

---

### Post by DSn0wMan on 2008-03-05
Same problem here, has anybody found an answer?

---

### Post by DSn0wMan on 2008-03-06
I ended up giving up on the ALSA driver. When I use the OSS driver I have no problems.

---

