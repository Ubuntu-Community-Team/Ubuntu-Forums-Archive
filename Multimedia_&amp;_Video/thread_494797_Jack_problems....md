---
title: "Jack problems..."
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by hseiken on 2007-07-07
Never have gotten this to work.  I turned on Verbose Messages and this is the output in the console...

```

09:58:04.912 /usr/bin/jackd -dalsa -ddefault -r44100 -p1024 -n2 -P/dev/dsp -o2 -M -O4
09:58:04.925 JACK was started with PID=9139 (0x23b3).
cannot write to jackstart sync pipe 4 (Bad file descriptor)
jackd: wait for startup process exit failed
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... /dev/dsp|-|1024|2|44100|0|2|nomon|hwmeter|-|32bit
ALSA lib control.c:910:(snd_ctl_open_noupdate) Invalid CTL /dev/dsp
control open "/dev/dsp" (No such file or directory)
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
09:58:04.936 JACK was stopped successfully.
09:58:04.936 Post-shutdown script...
09:58:04.937 killall jackd
jackd: no process killed
09:58:05.126 MIDI connection change.
09:58:05.145 Post-shutdown script terminated with exit status=256.
09:58:07.168 Could not connect to JACK server as client. Please check the messages window for more info.
09:59:31.476 JACK is starting...
09:59:31.476 /usr/bin/jackd -v -dalsa -dhw:0 -r44100 -p1024 -n2 -P/dev/dsp -o2 -M -O4
09:59:31.479 JACK was started with PID=9183 (0x23df).
cannot write to jackstart sync pipe 4 (Bad file descriptor)
jackd: wait for startup process exit failed
getting driver descriptor from /usr/lib/libjack0.100.0/jack_alsa.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_oss.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_dummy.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_freebob.so
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
apparent rate = 44100
creating alsa driver ... /dev/dsp|-|1024|2|44100|0|2|nomon|hwmeter|-|32bit
ALSA lib control.c:910:(snd_ctl_open_noupdate) Invalid CTL /dev/dsp
control open "/dev/dsp" (No such file or directory)
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via gettimeofday
required capabilities not available
capabilities: =
new client: alsa_pcm, id = 1 type 1 @ 0x805adf8 fd = -1
starting server engine shutdown
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
no message buffer overruns
cleaning up shared memory
cleaning up files
unregistering server `default'
09:59:31.516 JACK was stopped successfully.
09:59:31.516 Post-shutdown script...
09:59:31.516 killall jackd
jackd: no process killed

```

Any ideas what's going on?  ALSA works fine for everything...except this.

---

