---
title: "getting jack server to run in rosegarden"
date: 2008-02-29
forum: Multimedia Production
---

### Post by david dawyth on 2008-02-29
Hi-
I am unable to get rosegarden to work because I cannot get jack server to run. On my first install of this distro (Unbuntu Studio....had the same problem with Audiocity (didnt work...and rosegarden worked....below is error message from Jack control any help is most welcome.

19:53:09.731 Statistics reset.
JACK tmpdir identified as [/dev/shm]
19:53:09.824 MIDI connection graph change.
19:53:09.961 MIDI connection change.
19:53:11.669 Startup script...
19:53:11.669 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
sound server terminated
19:53:11.952 Startup script terminated successfully.
19:53:11.952 JACK is starting...
19:53:11.953 /usr/bin/jackd -dalsa -r44100 -p512 -n2 -D -C/dev/dsp -P/dev/dsp
19:53:11.956 JACK was started with PID=10530 (0x2922).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... /dev/dsp|/dev/dsp|512|2|44100|0|0|nomon|swmeter|-|32bit
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/dsp
control open "/dev/dsp" (No such file or directory)
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
19:53:12.033 JACK was stopped successfully.
19:53:12.034 Post-shutdown script...
19:53:12.034 killall jackd
jackd: no process killed
19:53:12.268 Post-shutdown script terminated with exit status=256.
19:53:13.988 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
.

---

### Post by david dawyth on 2008-02-29
sorry it unbuntu studio 7.10

---

### Post by kish on 2008-02-29
This helped me 

qjackctl-0.3.1a-5

but on different circumstances.

---

### Post by david dawyth on 2008-02-29
ty but tried....gives same error code(s)

---

### Post by solarwind on 2008-03-02
I also am unable to get rosegarden working.

---

### Post by js72 on 2008-03-02
Hey guys and gals take a look at this:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

It has always helped me to get going. Especially take a look at  realtime support and alsasequencer section.

---

### Post by Stochastic on 2008-03-02
> **david dawyth said:**
> 
creating alsa driver ... /dev/dsp|/dev/dsp|512|2|44100|0|0|nomon|swmeter|-|32bit
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/dsp
control open "/dev/dsp" (No such file or directory)
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
.

That error message tells you that JACK wasn't able to get the soundcard you pointed it to open.  My first guess to fix this would be to go into qjackctl setup panel and change your Input Device and Output Device to hw:0 rather than /dev/dsp.  Secondly make sure no other apps are open that might use that soundcard (including firefox if you've played a flash movie recently).

---

