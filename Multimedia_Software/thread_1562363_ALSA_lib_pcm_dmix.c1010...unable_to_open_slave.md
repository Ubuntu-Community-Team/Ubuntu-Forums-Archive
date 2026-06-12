---
title: "ALSA lib pcm_dmix.c:1010:...unable to open slave"
date: 2010-08-27
forum: Multimedia Software
---

### Post by byro-byro on 2010-08-27
Hi.
Trying to use Rosegarden/Qsynth/QJackctl I get no sound - the Qsynth message presents "ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave". Ardour is failling too.
I see an old thread about this and test all the procedures suggested there (install libsdl1.2deb.all, purge pulseaudio...). Doesn't work for me.
Alsamixer is all unmuted and in the end of the alsa-base file "options snd_hda-intel index=0" is added.
Sounds of system are working, also Audacious, and testing Alsa on terminal (aplay ...) is all fine.
My card is Intel 82801AA-ICH I running Ubuntu10.04 in a VBox.

Thanks

---

### Post by cchhrriiss121212 on 2010-08-28
Do you have jack running OK? Ardour and qsynth both rely on jack to function, so make sure you do not have any other programs running when starting jack. It would help if you could post the output of the message window. 

It could be a problem stemming from vbox, as hardware cannot directly talk to Ubuntu. If you want to record music with Ubuntu, virtualisation is not a great way to do it.

---

### Post by byro-byro on 2010-08-28
Yes I think Jack is fine. At moment without realtime. Qjackctl is the first starts, and then Qsynth or Ardour. The message (on the title of this thread) comes when the soundfonts (Fluidsynth) are load on Qsynth (that's a Qsynth message). 
There is no one program running before Jack and after just the necessary, Rosegarden needs one more program (I use Qsynth). The problems seems to be more then one program trying to access the card.  

Here is Jack message
14:17:55.338 Logging started --- Sat Aug 28 14:17:55 2010 ---
14:17:55.444 Patchbay deactivated.
14:17:55.464 Statistics reset.
14:17:55.609 Startup script...
14:17:55.613 artsshell -q terminate
14:17:55.640 ALSA connection graph change.
sh: artsshell: not found
14:17:56.027 Startup script terminated with exit status=32512.
14:17:56.028 JACK is starting...
14:17:56.029 /usr/bin/jackd -v -r -dalsa -r44100 -p1024 -n3 -D -Chw:0 -Phw:0 -S -Xraw
14:17:56.058 JACK was started with PID=1379.
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    382011
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
14:17:56.243 ALSA active patchbay scan...
14:17:56.250 ALSA connection change.
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_alsa.so
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
new client: alsa_pcm, id = 1 type 1 @ 0x9441128 fd = -1
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|16bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 3 periods for playback
14:17:56.462 ALSA active patchbay scan...
new buffer size 1024
registered port system:capture_1, offset = 4096
registered port system:capture_2, offset = 8192
registered port system:playback_1, offset = 0
registered port system:playback_2, offset = 0
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
-- jack_sort_graph
1379 waiting for signals
14:17:58.327 Server configuration saved to "/home/marcelo/.jackdrc".
14:17:58.332 Statistics reset.
14:17:58.334 Client activated.
14:17:58.340 JACK connection change.
14:17:58.357 JACK connection graph change.
14:17:58.360 XRUN callback (1).
server thread back from poll
new client: qjackctl, id = 2 type 2 @ 0xb77fd000 fd = 20
start poll on 4 fd's
server thread back from poll
new client qjackctl using 23 for events
start poll on 4 fd's
server thread back from poll
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
+++ client is now qjackctl active ? 1
client qjackctl: start_fd=7, execution_order=0.
client event poll on 23 for qjackctl starts at 238378085
back from client event poll after 1 usecs
client qjackctl: wait_fd=17, execution_order=1 (last client).
-- jack_rechain_graph()
-- jack_sort_graph
start poll on 4 fd's
client event poll on 23 for qjackctl starts at 238382964
back from client event poll after 278 usecs
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
client event poll on 23 for qjackctl starts at 238455901
back from client event poll after 186 usecs
client event poll on 23 for qjackctl starts at 238527714
back from client event poll after 448 usecs
14:17:58.541 JACK active patchbay scan...
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
client event poll on 23 for qjackctl starts at 238598285
back from client event poll after 225 usecs
...  
Thanks

---

### Post by cchhrriiss121212 on 2010-08-28
Jack will perform better with realtime mode enabled, so to do that:
```
sudo gedit /etc/security/limits.d/audio.conf
```
then paste this at the bottom:
@audio - rtprio 99
@audio - memlock unlimited

If you don't get any improvement then I would say it is down to Vbox limitations.

---

