---
title: "Can not connect to Jack Sever"
date: 2008-01-11
forum: Multimedia Production
---

### Post by Simonridesbikes on 2008-01-11
when i load up the JACK audio connection kit everything loads fine i click start it seems to connect but then i get an error message saying the connection has failed with this in the dialogue box


15:39:11.469 Patchbay deactivated.
15:39:11.473 Statistics reset.
15:39:11.505 MIDI connection graph change.
JACK tmpdir identified as [/dev/shm]
15:39:11.681 MIDI connection change.
15:39:12.647 Startup script...
15:39:12.647 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
15:39:12.869 Startup script terminated with exit status=256.
15:39:12.869 JACK is starting...
15:39:12.869 jackd -R -doss -r22050 -p1024 -n3 -w16
15:39:12.870 JACK was started with PID=7733 (0x1e35).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
OSS: failed to open device /dev/dsp: oss_driver.c@526, errno=16
cannot start driver
15:39:12.980 JACK was stopped successfully.
15:39:12.980 Post-shutdown script...
15:39:12.980 killall jackd
jackd: no process killed
15:39:13.187 Post-shutdown script terminated with exit status=256.
15:39:14.900 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]

I don't really understand it can any one help
thanks
simon
:guitar:
(it seemed cool as its a music question :))

---

### Post by urangela on 2008-01-27
It is possible that something (like oss) is using your sound card, and you can't actually see the program, For example, If I were to be playing a a game with sound, And I then tried to start the jack server, I would get exactly that output in the message window, For a while I had a problem with the game Kobodeluxe. Where I would quit the game, but got this error when I tried to start Jack. I opened up the system monitor, and the process for the game was still running. After killing the process Jack started fine. 
    My general impression of this error message is that it means that somehow Jack is being prevented from connecting to the sound card  which (and someone please correct me if I am wrong) is accomplished by alsa. A patch diagram might look like:

[audio output from programs ie ardour, audacity etc...] -> [Jack] -> [Alsa] -> [sound card/speakers].

What system are you using, and what sound card do you have?

---

### Post by urangela on 2008-01-27
I just took another look at your error message and noticed:

> OSS: failed to open device /dev/dsp: oss_driver.c@526, errno=16
cannot start driver

It looks like you have the oss driver selected, try changing your driver to ALSA, when you open Jack, click on setup and you should see a dropdown menu labled "Driver:" that has several different options, select alsa hit Ok and then try and restart the Jack server with the play button.

---

### Post by hihihi on 2008-02-07
funny 
i got the same message since ubuntu gutsy.
i try to start up jack with oss instead of alsa, which was possible half year ago, but since gutsy i get this message:

OSS: failed to open device /dev/dsp: oss_driver.c@526, errno=16
cannot start driver

any ideas????

---

### Post by urangela on 2008-02-16
Its possible that gutsy doesn't have any of the older oss drivers built in. ALSA is supposed to have builtin oss support, and be back-compatible with any applications that still use oss. I would try running your oss apps with alsa and see what happens.

---

