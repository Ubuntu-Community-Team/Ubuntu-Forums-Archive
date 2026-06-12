---
title: "JACK problems"
date: 2008-03-06
forum: Multimedia Production
---

### Post by Skiddy85 on 2008-03-06
Having lots of problems with JACK.
Computer: Intel Q6600, ASUS P5N32-E SLI mobo, (includes on board audio), linux on 80G hd, Asus 8800 gts 320mb graphics, 2 gb RAM, X mystique sound card, Ubuntu studio 7.10.

Using the on board sound, whenever using JACK the sound crackles. Doesn't matter what settings, and no Xruns. Sound doesn't crackle when not using jack. For the x mystique, whenever not using jack, sound works normally no problems, but jack when started all sorts of weird things. When  using 1024/period and 2 periods per buffer, get 42 Xruns every 2 seconds, and won't start transporting. By increasing these numbers, can get xruns to 18 every 2s, but will transport, no sound apparent, and 185ms latency. Won't start if I adjust any other setting, except the real time switch, which will start but not allow transport. 

Example message output:

15:00:46.301 Startup script...
15:00:46.301 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Creating link /home/steven/.kde/socket-steven.
15:00:46.521 Startup script terminated with exit status=256.
15:00:46.521 JACK is starting...
15:00:46.521 jackd -v -R -P10 -dalsa -dhw:0 -r44100 -p1024 -n2
15:00:46.522 JACK was started with PID=6938 (0x1b1a).
getting driver descriptor from /usr/lib64/jack/jack_oss.so
getting driver descriptor from /usr/lib64/jack/jack_alsa.so
getting driver descriptor from /usr/lib64/jack/jack_freebob.so
getting driver descriptor from /usr/lib64/jack/jack_dummy.so
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
new client: alsa_pcm, id = 1 type 1 @ 0x614190 fd = -1
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
new buffer size 1024
registered port alsa_pcm:capture_1, offset = 4096
registered port alsa_pcm:capture_2, offset = 8192
registered port alsa_pcm:playback_1, offset = 0
registered port alsa_pcm:playback_2, offset = 0
registered port alsa_pcm:playback_3, offset = 0
registered port alsa_pcm:playback_4, offset = 0
registered port alsa_pcm:playback_5, offset = 0
registered port alsa_pcm:playback_6, offset = 0
registered port alsa_pcm:playback_7, offset = 0
registered port alsa_pcm:playback_8, offset = 0
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
6938 waiting for signals
15:00:47.714 Server configuration saved to "/home/steven/.jackdrc".
15:00:47.714 Statistics reset.
15:00:47.715 Client activated.
15:00:47.715 Audio connection change.
15:00:47.718 Audio connection graph change.
new client: qjackctl-6729, id = 2 type 2 @ 0x2aaaaaaab000 fd = 15
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
client qjackctl-6729: start_fd=5, execution_order=0.
client qjackctl-6729: wait_fd=10, execution_order=1 (last client).
-- jack_rechain_graph()
JACK tmpdir identified as [/dev/shm]
SSE2 detected
15:00:47.755 XRUN callback (1).
15:00:48.992 Transport start.
15:00:49.122 XRUN callback (29 skipped).
15:00:51.131 XRUN callback (42 skipped).
15:00:51.384 Transport start.
15:00:51.533 XRUN callback (8 skipped).
jackd watchdog: timeout - killing jackd
zombified - calling shutdown handler
15:00:51.623 Shutdown notification.
15:00:51.623 Client deactivated.
15:00:51.623 JACK was stopped successfully.
15:00:51.624 Post-shutdown script...
15:00:51.624 killall jackd
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)
jackd: no process killed
15:00:51.835 Post-shutdown script terminated with exit status=256.

Any help getting this to work would be greatly apprecited.
Cheers
Skiddy

---

### Post by Alarindris on 2008-03-12
I've got the same problem.

---

