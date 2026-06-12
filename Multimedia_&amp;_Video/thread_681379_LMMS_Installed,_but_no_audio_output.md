---
title: "LMMS Installed, but no audio output"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by djrobthaman on 2008-01-28
Let me preface this with the fact that I have used lmms before and remember having a similar problem and fixing it (I think) by installing jack and somehow having that server run before I turned on lmms.

But that isn't working (or at least I can't get it to work).

So here's the story.  I've installed lmms.  But whenever I open it the settings window comes up and says it is using the dummy audio output.  If I change it to alsa it says the change will only be detected with a restart of the program.  I restart the program and then I'm back at square one again, with dummy audio output selected.

I get no audio output from lmms no matter whether I select alsa.

Whenever I start lmms from the terminal I get

```

douglas@douglas-desktop:~$ lmms
could not set realtime priority.
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Playback open error: Device or resource busy
No audio-driver working - falling back to dummy-audio-driver
You can render your songs and listen to the output files...

```

Like I said before I have installed jack (jackEQ and jackControl) and no matter what settings in Jack Control I try it says "Could not connect to Jack serveras client."  and the msg window gives

```

22:54:23.458 Patchbay deactivated.
22:54:23.478 Statistics reset.
22:54:23.538 MIDI connection graph change.
JACK tmpdir identified as [/dev/shm]
22:54:23.710 MIDI connection change.
22:54:24.790 Startup script...
22:54:24.790 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
22:54:25.038 Startup script terminated with exit status=256.
22:54:25.038 JACK is starting...
22:54:25.038 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n3
22:54:25.051 JACK was started with PID=8720 (0x2210).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
22:54:25.056 JACK was stopped successfully.
22:54:25.057 Post-shutdown script...
22:54:25.057 killall jackd
jackd: no process killed
22:54:25.267 Post-shutdown script terminated with exit status=256.
22:54:27.171 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]

```

I don't know if the info on Jack helps, but I figured I should include it.

Does anyone know how I can get lmms to give audio output (preferably without having to use jack).  It would be great if I could just turn lmms on, and it would all work instead of having to load something else before it.

Thanks a bunch,
Douglas

---

### Post by djrobthaman on 2008-01-28
Okay... so for some reason, if I turn off Hydrogen (yes I was running Hydrogen at the same time)  I can get audio output, but it is very staticy.  Any suggestions on how to:

1.  get rid of the static
2.  Have both these programs run simultaneously without a problem.

Thanks again.

---

