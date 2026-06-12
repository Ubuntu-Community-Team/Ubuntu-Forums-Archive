---
title: "jack problem"
date: 2008-03-01
forum: Multimedia Production
---

### Post by lolzlolz on 2008-03-01
JACK is having problems on my computer, when i have JACK running all my sound becomes crackly and also the main reason i have JACK running is for rosegarden, well while in rosegarden JACK causes there to be no sound from rosegarden it acts like its playing but no sound comes out, i cant figure out why, could you help?
thanks

---

### Post by lolzlolz on 2008-03-02
bump

---

### Post by Stochastic on 2008-03-02
a couple questions for clairification:

1) are you starting jack before starting rosegarden?

2) are other apps able to play through jack?

3) what soundcard are you running?

4) can you post a screenshot of (or list off) the settings window in qjackctl?

---

### Post by lolzlolz on 2008-03-02
yes i am starting jack before rosegarden, i have also tried having rosegarden start it

i dont know if other apps can, what program should  i use to test that?

my soundcard is a built into motherboard card specifically,  it is 7.1 channel, Azalia (hda)

screenshot is attached

note: i will try from a non realtime kernel, also if i set qjacktl to realtime it cant start jack

---

### Post by robeast on 2008-03-02
Increasing latency usually solves crackly audio with JACK. Try increasing your Frames/period to knock the latency up a notch and take some of the stress off of your integrated sound card. Also boosting JACK's priority (higher number) can help.

What are you playing through Rosegarden? Do you have audio or have you sequenced MIDI notes? If you did MIDI you need to send that data to a synth to get sound from it.

---

### Post by lolzlolz on 2008-03-02
ok non rt kernel does same thing,
in rosegarden i am just making notes/using matrix editor and playing it so i would assume this is midi, also hydrogen works and i assume that uses jack and i still get sound so, i will do the changes to jack
and how do i send it to a synth?
thanks

---

### Post by lolzlolz on 2008-03-02
after bumping up the latency as you suggested i get the following error

```

17:15:57.108 Patchbay deactivated.
17:15:57.111 Statistics reset.
JACK tmpdir identified as [/dev/shm]
17:15:57.144 MIDI connection graph change.
17:15:57.322 MIDI connection change.
17:16:10.870 Startup script...
17:16:10.870 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Link points to "/tmp/ksocket-lexor"
17:16:11.285 Startup script terminated with exit status=256.
17:16:11.285 JACK is starting...
17:16:11.285 jackd -dalsa -dhw:0 -r44100 -p2048 -n2
17:16:11.286 JACK was started with PID=9650 (0x25b2).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|2048|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 2048 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: cannot set period size to 2048 frames for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
no message buffer overruns
17:16:11.369 JACK was stopped successfully.
17:16:11.369 Post-shutdown script...
17:16:11.369 killall jackd
jackd: no process killed
17:16:11.575 Post-shutdown script terminated with exit status=256.
17:16:13.298 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
```

---

### Post by robeast on 2008-03-04
Dang...I don't know what yo tell you. My experience with JACK has been pretty hassle free, so I haven't had to learn much about the technical aspects of it. Have you had any luck yet? I noticed in your other post you are using your normal computer speakers, which work until you turn on JACK. Unless you want to route your audio and MIDI signals around to other programs, you don't even need to use JACK at all.

---

### Post by Stochastic on 2008-03-04
try switching your frames/period back to 1024, but turning your period/buffer to 3.

also, try checking the realtime box (if you're running the realtime kernel) and setting your port/maximum to 512.

Really, these are just educated guesses as to what will fix the problem.  Each soundcard/computer has it's own perfect happy setting in JACK.  It'd be nice if the qjackctl devs built an autoconf button that tries out a whole bunch of options to see what works best, but until then we kinda have to just do that process ourselves.

---

### Post by lolzlolz on 2008-03-05
ok i made the suggested settings and it had another error :(
```

06:55:25.922 Patchbay deactivated.
06:55:25.932 Statistics reset.
JACK tmpdir identified as [/dev/shm]
06:55:25.991 MIDI connection graph change.
06:55:26.142 MIDI connection change.
06:56:08.366 Startup script...
06:56:08.366 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Link points to "/tmp/ksocket-lexor"
06:56:08.715 Startup script terminated with exit status=256.
06:56:08.715 JACK is starting...
06:56:08.715 jackd -R -P89 -dalsa -dhw:0 -r44100 -p1024 -n3
06:56:08.716 JACK was started with PID=3252 (0xcb4).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread 1745456560, from thread 1745456560] (1: Operation not permitted)
cannot create engine
06:56:08.739 JACK was stopped successfully.
06:56:08.739 Post-shutdown script...
06:56:08.739 killall jackd
jackd: no process killed
06:56:08.946 Post-shutdown script terminated with exit status=256.
06:56:10.728 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm
```

no i havent got it working yet, the max for the port/maximum for my comp was 89 thanks

---

### Post by Stochastic on 2008-03-05
hmm, seems like your account doesn't have realtime privileges (I forget right now how to allow this).

Also, you've mixed up what I said a bit.. set your port/maximum to 512 not your priority.  A higher priority will affect how important in the realtime kernel's schedule the audio process is - I've got mine set to 70 - but you don't need to worry about that until you get realtime privileges.

---

### Post by lolzlolz on 2008-03-05
o oops, ill fix that
when u remember how to give privelages tell me, 
thanks
once i fixed that it gave this issue
```

19:42:25.993 Patchbay deactivated.
19:42:25.997 Statistics reset.
JACK tmpdir identified as [/dev/shm]
19:42:26.020 MIDI connection graph change.
19:42:26.202 MIDI connection change.
19:42:56.165 Startup script...
19:42:56.165 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Creating link /home/lexor/.kde/socket-lexor-ubuntu.
19:42:56.582 Startup script terminated with exit status=256.
19:42:56.582 JACK is starting...
19:42:56.582 jackd -p512 -dalsa -dhw:0 -r44100 -p1024 -n3
19:42:56.583 JACK was started with PID=22368 (0x5760).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames, buffer = 3 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: got smaller periods 2 than 3 for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
no message buffer overruns
19:42:56.673 JACK was stopped successfully.
19:42:56.674 Post-shutdown script...
19:42:56.674 killall jackd
jackd: no process killed
19:42:56.880 Post-shutdown script terminated with exit status=256.
19:42:58.596 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
```

---

### Post by lolzlolz on 2008-03-08
ok i will test on my laptop, i could try getting a new soundcard to fix the problems right???

---

### Post by lolzlolz on 2008-03-09
what soundcards support midi and are pcie cuz i habe 3 empty pcie slots on my comp cuz i just used on  mobo  card when i built the comp so any recommendations?
thanks

---

### Post by Stochastic on 2008-03-09
There are tons out there that work great with linux. Basically check out the [http://www.alsa-project.org](http://www.alsa-project.org) website and see what cards are compatible.  Then it's a matter of quality/price choice.  M-Audio tend to be quite good for lower budgets.

---

### Post by lolzlolz on 2008-03-10
thx
im gonna test my mom's old broken one that i replaced and see if it even works for normal sound (however i think it's fried) if that doesnt work i may get a new one, but currently it seems ot be working without jack

---

