---
title: "Jack, a dell, and xruns galore"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by ronlybonly on 2006-10-29
I just got a new Dell Inspiron E1705 laptop, and of course, I immediately installed Dapper. I got everything woring great... with the exception of Jack (my single most-used app). When I try to start it up, it runs for about 3 seconds, spits out somewhere in the neighborhood of 150-250 Xruns, then aborts. ](*,) 

```

23:01:39.604 Patchbay deactivated.
23:01:39.744 Statistics reset.
23:01:39.954 MIDI connection graph change.
23:01:39.986 MIDI connection change.
23:01:43.019 Startup script...
23:01:43.019 artsshell -q terminate
sound server terminated
23:01:43.325 Startup script terminated successfully.
23:01:43.325 JACK is starting...
23:01:43.326 /usr/bin/jackd -v -R -p64 -t10000 -dalsa -dhw:0 -r44100 -p64 -n4 -D -Chw:0,0
23:01:43.353 JACK was started with PID=17935 (0x460f).
23:01:43.361 Could not connect to JACK server as client. Please check the messages window for more info.
getting driver descriptor from /usr/lib/libjack0.100.0-0/jack_alsa.so
getting driver descriptor from /usr/lib/libjack0.100.0-0/jack_dummy.so
getting driver descriptor from /usr/lib/libjack0.100.0-0/jack_oss.so
jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
registered builtin port type 32 bit float mono audio
required capabilities not available
capabilities: =
new client: alsa_pcm, id = 1 type 1 @ 0x80586e8 fd = -1
apparent rate = 44100
creating alsa driver ... hw:0|hw:0,0|64|4|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 64 frames, buffer = 4 periods
nperiods = 4 for capture
nperiods = 4 for playback
new buffer size 64
registered port alsa_pcm:capture_1, offset = 256
registered port alsa_pcm:capture_2, offset = 512
registered port alsa_pcm:playback_1, offset = 0
registered port alsa_pcm:playback_2, offset = 0
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
17935 waiting for signals
23:01:45.050 Server configuration saved to "/home/meredithas/.jackdrc".
23:01:45.052 Statistics reset.
23:01:45.451 Client activated.
23:01:45.461 Audio connection change.
23:01:45.478 Audio connection graph change.
23:01:45.480 XRUN callback (1).
23:01:45.481 XRUN callback (2).
new client: qjackctl-17931, id = 2 type 2 @ 0xb7f86000 fd = 15
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
client qjackctl-17931: start_fd=5, execution_order=0.
client qjackctl-17931: wait_fd=10, execution_order=1 (last client).
-- jack_rechain_graph()
23:01:47.502 XRUN callback (101 skipped).
jackd watchdog: timeout - killing jackd
23:01:48.598 Shutdown notification.
23:01:48.610 Client deactivated.
23:01:48.614 JACK was stopped successfully.
zombified - calling shutdown handler
cannot read result for request type 7 from server (Connection reset by peer)
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)

```

Does anybody know how to fix this?

---

### Post by Firefox79 on 2006-10-30
What soundcard do you have? I had a similar problem once. In my case (with a Intel ICH6) the solution was to switch to 48kHz.
Oh and don't forget to stop the powernowd since switching the cpu frequency is obviously not a good thing for realtime processing.

Cheers

---

### Post by ronlybonly on 2006-10-30
I have a Creative Sound Blaster Audigy HD Software edition. It works just fine with ALSA, but for whatever reason, jack is being pretty ornery. I have tried every samplerate available, but it doesn't seem to change anything. I also tried uninstalling jack and reboilding it from source - no luck there either.

---

### Post by ronlybonly on 2006-11-03
Is this probably a soundcard problem? Keep in mind that ALSA works like a charm on my machine. I'm sure I'm just overlooking some stupid little obvious detail, but I can't figure out what it is.

---

