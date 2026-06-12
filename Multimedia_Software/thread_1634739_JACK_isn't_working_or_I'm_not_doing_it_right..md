---
title: "JACK isn't working or I'm not doing it right."
date: 2010-11-30
forum: Multimedia Software
---

### Post by The Eight-Bit Link on 2010-11-30
Same as above. I've fiddled around, but I can't get Rosebud to work. I have Qsynth, ZynAddSubFX Synth, JACK control, and Rosebud but I can't get any of it to work

---

### Post by cchhrriiss121212 on 2010-12-01
Is jack starting without error? Could you please post the ouptut of the jack message window.
I have googled Rosebud but I'm not sure it has anything to do with jack. Did you mean Rosegarden?

---

### Post by Evil-Ernie on 2010-12-01
Ive also had a problem with Qsynth not producing sound, midi is fine and signals are received but it just doesnt seem to be outputting sound to Jack while everything else sound wise is fine

---

### Post by heldal on 2010-12-01
A couple things to keep in mind with jack and qsynth:

1. Use qjackctl (JACK Control in the sound menu) for setup and make sure jack attaches to the correct audio interface (in case there is more than one). Use the same soundcard for input and output in the basic setup or you'll have sync problems. If you have additional soundcards add them with alsa_in and alsa_out whenever necessary. Advanced users use scripts to perform tasks pre/post jack start/stop. With scripts you can also enable pulseaudio output through jack for audio from desktop apps.

2. By default Qsynth connects to Jack, but doesn't attach to any particular device. You have to connect the outputs manually in qjackctl. Qsynth can be configured to connect its outputs automatically, in which case it picks the first 2 available sound-channels which in turn may or may not be the correct ones in a surround-sound or multi-card setup.

3. The desktop volume control (pulseaudio) does not control the hardware directly and becomes useless when jack has been started. Use alsamixer in a terminal instead (or install an alsa-mixer with GUI for this purpose). There will be no sound through jack if the audio-channel on the soundcard is muted.

---

### Post by Evil-Ernie on 2010-12-01
Cheers I will give it a go tonight

---

### Post by The Eight-Bit Link on 2010-12-01
I tried it this morning and it seems to be working.
However, after I turned off JACK, my sound stopped working (Exaile, Flash, system alert sounds)

---

### Post by heldal on 2010-12-01
> **The Eight-Bit Link said:**
> 
However, after I turned off JACK, my sound stopped working (Exaile, Flash, system alert sounds)

That's pulseaudio for you. It isn't very cooperative and crashes frequently if/when other processes disturbs its interaction with audio applications and devices. I've concluded that it is best to try to restore it to a "known state" after jack has been started and after jack is stopped.

jack-pre-start.sh is executed before jackd starts:
```
#!/bin/sh
killall pulseaudio
```

jack-post-start.sh is executed after jackd starts and reloads pulseaudio and prepares it to use jack for input and output. Some pauses are necessary to give processes started in the background some time to initiate:
```
#!/bin/sh
pulseaudio -D
sleep 2
pactl load-module module-jack-sink channels=2
pactl load-module module-jack-source channels=2
sleep 2
pacmd set-default-sink jack_out
```

jack-pre-shutdown.sh stops everything that should be stopped before jackd shuts down:
```
#!/bin/sh
killall pulseaudio
```

jack-post-shutdown.sh make sure jack is stopped, restarts pulseaudio and points its output to the default soundcard
```
#!/bin/sh
killall jackd
sleep 1
pulseaudio -D
sleep 1
pacmd set-default-sink 0
```

These scripts are then made executable and referred to from the setup in qjacktctl. Alternatively combine them into scripts to start and stop jack if you prefer that over qjacktctl. Check with the default sound-pref-app that audio in/out for the desktop is pointing to the right places when the start or stop procedures are completed. Any audio-applications which are left running during the switch may hang or crash. Applications which close the audio-device when paused (e.g. rhythmbox) may be left in paused state during the switch.

---

### Post by The Eight-Bit Link on 2010-12-04
Now it's complaining it can't connect to a server. 
p, li { white-space: pre-wrap; }```
18:37:46.600 Startup script...
 18:37:46.603 /home/jd/Programs/JACK/startbefore.sh
 sh: /home/jd/Programs/JACK/startbefore.sh: Permission denied
 18:37:47.072 Startup script terminated with exit status=32256.
 18:37:47.074 JACK is starting...
 18:37:47.075 /usr/bin/jackd -m -dalsa -dhw:0 -r44100 -p1024 -n2 -Xseq
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    1546278
 18:37:47.131 JACK was started with PID=3720.
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
 cannot load driver module alsa
 18:37:47.227 JACK was stopped successfully.
 18:37:47.229 Post-shutdown script...
 18:37:47.230 /home/jd/Programs/JACK/killafter.sh
 sh: /home/jd/Programs/JACK/killafter.sh: Permission denied
 18:37:47.640 Post-shutdown script terminated with exit status=32256.
 18:37:49.380 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

```
Here is the output in the Messages box

---

### Post by cchhrriiss121212 on 2010-12-04
> the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
Here is the problem. You just need to shut down any other programs that use audio (VLC, Firefox etc.) before starting jack.

---

### Post by The Eight-Bit Link on 2010-12-05
Kay, So nothing is running except Jack, and I get this output
p, li { white-space: pre-wrap; }```
13:55:36.339 Patchbay deactivated.
 13:55:36.341 Statistics reset.
 13:55:36.816 ALSA connection graph change.
 13:55:37.335 ALSA connection change.
 13:56:47.409 Startup script...
 13:56:47.416 artsshell -q terminate
 sh: artsshell: not found
 13:56:47.835 Startup script terminated with exit status=32512.
 13:56:47.837 JACK is starting...
 13:56:47.843 /usr/bin/jackd -u -dalsa -dhw:0 -r44100 -p1024 -n2 -Xseq
 13:56:47.856 JACK was started with PID=21945.
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    1546278
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 13:56:50.929 Server configuration saved to "/home/jd/.jackdrc".
 13:56:50.931 Statistics reset.
 13:56:51.416 Client activated.
 13:56:51.444 JACK connection graph change.
 13:56:51.447 Buffer size change (1024).
 configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 16bit little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 16bit little-endian
 ALSA: use 2 periods for playback
 13:56:51.614 ALSA connection graph change.
 13:56:51.636 XRUN callback (1).
 13:56:51.667 JACK connection change.
 13:56:53.476 XRUN callback (18 skipped).
 13:56:55.481 XRUN callback (19 skipped).
 13:56:57.485 XRUN callback (19 skipped).
 13:56:59.489 XRUN callback (19 skipped).
 jackd watchdog: timeout - killing jackd
 13:57:01.494 XRUN callback (19 skipped).
 13:57:01.758 Shutdown notification.
 13:57:01.762 JACK is stopping...
 13:57:01.764 JACK is being forced...
 cannot continue execution of the processing graph (Resource temporarily unavailable)
 zombified - calling shutdown handler
 13:57:01.897 ALSA connection graph change.
 13:57:01.931 ALSA connection graph change.
 13:57:02.189 JACK was stopped with exit status=1.
 13:57:02.191 Post-shutdown script...
 13:57:02.200 killall jackd
 13:57:02.221 ALSA connection graph change.
 jackd: no process found
 13:57:02.722 Post-shutdown script terminated with exit status=256.

```
Often it just freezes after watchdog shuts it down

---

### Post by cchhrriiss121212 on 2010-12-05
XRUNs mean that your system cannot handle the audio at this latency, so try raising the frames value in setup. Also make sure you have realtime and soft mode boxes checked.

---

### Post by The Eight-Bit Link on 2010-12-05
Watchdog keeps timing out, how do I stop that from happening?

---

### Post by The Eight-Bit Link on 2010-12-07
Bumped because I need this and it keeps timing out.
It didn't do this before an update, and now it is...

---

### Post by cchhrriiss121212 on 2010-12-07
Could you explain the problem a bit more? What are you using watchdog for? Do you see any error messages? Have you tried to increase the timeout variable in qjackctl setup?

---

### Post by The Eight-Bit Link on 2010-12-08
I've increased it to 5000 ms, the max without watchdog complaining.
this is what happens when it shuts down.
p, li { white-space: pre-wrap; }```
20:30:41.055 JACK connection change.
 20:30:41.076 JACK connection graph change.
 20:30:41.166 ALSA connection graph change.
 jackd watchdog: timeout - killing jackd
 20:30:51.339 Shutdown notification.
 20:30:51.372 JACK is stopping...
 20:30:51.374 JACK is being forced...
 cannot continue execution of the processing graph (Resource temporarily unavailable)
 zombified - calling shutdown handler
 20:30:51.472 ALSA connection graph change.
 20:30:51.517 ALSA connection graph change.
 20:30:52.200 JACK was stopped with exit status=1.
 20:30:52.212 Post-shutdown script...
 20:30:52.217 killall jackd
 jackd: no process found
 20:30:52.781 Post-shutdown script terminated with exit status=256.

```

---

### Post by cchhrriiss121212 on 2010-12-09
I have looked it up and found 2 packages called watchdog, so which one are you using?
Try opening it from a terminal and then post the output.

---

