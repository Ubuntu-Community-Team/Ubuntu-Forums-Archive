---
title: "Bluetooth audio and Pulseaudio problem"
date: 2009-03-27
forum: Multimedia Software
---

### Post by Scubdup on 2009-03-27
I am trying to stream sound through my computer and then via a bluetooth receiver, to my hifi.

I followed HyRax's excellent instructions [here]("http://forums.overclockers.com.au/showthread.php?t=694010"). A couple of things didn't go as they should but I ignored them or tweaked the instructions and the end result was fine. Glorious audio, first time round!

Some time later I restarted the machine and I've nevber been able to get back to nirvana.

After adopting a bit of a scattergun approach to which instructions I'd need to repeat after a restart, I was able to play audio via bluetooth using the command:

```
$ aplay -D bluetooth -f s16_le /usr/share/sounds/login.wav
```

However, I cannot get Spotify or Rhythmbox to do the same.

My limited investigations have come up with some theories and evidence:

Under PulseAudio Device Chooser, when I try to do a left-click on the jack icon and a menu appears. In this menu, choose "Manager". A new window appears. At the bottom it reads: "Failure: Connection refused"

After googling I tried:

```
pulseaudio -D
```

And got some errors. The same page recommended to restart and try 

```
pulseaudio -D
```

again, which I did and got the following errors:

```
~$ pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: daemon startup failed.

```
I think this must be where the problem lies.

Any help would be very gratefully received. Many thanks.

---

### Post by markbuntu on 2009-03-27
Try pulseaudio -vvv to see a more verbose ouput that may pinpoint why the pulse daemon will not start.

---

### Post by Scubdup on 2009-03-27
> **markbuntu said:**
> Try pulseaudio -vvv to see a more verbose ouput that may pinpoint why the pulse daemon will not start.
Thanks

```
pulseaudio -vvv
I: main.c: PolicyKit refuses acquire-high-priority privilige.
I: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally required. If you experience crackling or other sound anomalies, consider one or more of the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed by policy. Disabling forcibly.
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
E: main.c: Unknown command: $ pactl load-module module-alsa-sink device=bluetooth
E: main.c: Failed to initialize daemon.
I: main.c: Daemon terminated.

```

---

### Post by Scubdup on 2009-03-27
I think that's helped. Hyrax has a warning in his instructions about this. Gonna investigate a bit further.

---

### Post by Scubdup on 2009-03-27
From Hyrax's instructions:

> 18.   Now we need to tell PulseAudio that your Bluetooth headset exists:
Code:

$ pactl load-module module-alsa-sink device=bluetooth
$ pactl load-module module-alsa-source device=bluetooth

Note that this enables your Bluetooth headset for PulseAudio only temporarily. To enable it permanently, create a new file using gedit ~/.pulse/default.pa and paste the two lines above into it and then save. [COLOR="Red"]NOTE: I've just noticed this tends to break PulseAudio because the bonding of your headset needs to have occured before issuing the above commands, or PulseAudio refuses to start upon reboot. Don't create this file (or delete/rename if you've already created it) and PulseAudio works fine again. To keep using your Bluetooth headset, move the file you created to your Desktop and make it executable. Once your Desktop has loaded and you've paired your headset, then execute the file by double-clicking on it to notify PulseAudio about the headset[/COLOR]. 
(Yes, it really was actually in red!)

---

