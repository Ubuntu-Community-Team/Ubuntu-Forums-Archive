---
title: "problem with jack"
date: 2011-05-22
forum: Multimedia Software
---

### Post by djembeing on 2011-05-22
I'm new to linux. I cant get jack to work. Can anyone help?  Im using ubuntu 10.10 on a gateway laptop.

this is what it says in jack's window

p, li { white-space: pre-wrap;```
00:48:28.140 Patchbay deactivated.
 00:48:28.188 Statistics reset.
 00:48:28.197 ALSA connection graph change.
 00:48:28.450 ALSA connection change.
 00:48:36.141 Startup script...
 00:48:36.142 artsshell -q terminate
 sh: artsshell: not found
 00:48:36.546 Startup script terminated with exit status=32512.
 00:48:36.546 JACK is starting...
 00:48:36.547 /usr/bin/jackd -r -t2000 -dalsa -dhw:0 -r44100 -p1024 -n2
 00:48:36.551 Could not start JACK. Sorry.
 00:48:40.026 JACK was stopped with exit status=255.
 00:48:40.029 Post-shutdown script...
 00:48:40.030 killall jackd
 jackd: no process found
 00:48:40.442 Post-shutdown script terminated with exit status=256.

```

---

### Post by djembeing on 2011-05-23
Anyone? I really need to get to work with Ardour.

---

### Post by backu on 2011-05-23
Is that all the error you get when starting jack?

---

### Post by djembeing on 2011-05-24
That's the entire message window.  
I have gotten Jack to work.  Just messing around, I changed the audio option in Jack's setup from duplex to playback only.  It works just fine now. However, in the future, I'll need to be able to record and listen at the same time.  (I assume that's what the duplex setting lets you do.)

Also, does anyone know how to get Firefox's flash player to play through Jack.  (so i can watch tutorials on youtube and hear both Ardour's output and youtube. or eventually apply effects to whatever I'm watching online.)

---

### Post by backu on 2011-05-24
It's possible your sound card doesn't support Duplex mode, or your input is single channel (mono), in which case, the default Inputs (which defaults 2) will cause an error and keep it from starting up.

---

### Post by djembeing on 2011-05-25
I'll check into that.  Before, when I had windows, i would record two separate channels, (I made a cable with an 8th inch jack that went to 2 xlr[mic cables]stereo) I could also play and record at the same time.  I think my hardware is capable of it.  factory laptop sound card.  I don't know how to find the details on it.  Still new.  Funny, a friend came over and i was showing off my setup and it made an *** of me.  Could not get any sound through jack.  jack would start, ardour would play (meter action and scrolling) no sound.  Then, restarted this morning, plays just fine.  Easy fix, restarting, but i'd like to prevent downtime like that.  I'd like to learn more to be able to set up a reliable system for my work (recording, editing, mixing).   I am very thankful that there is such a support community for ubuntu. I wish i knew even a fraction of what some of these guys do.

---

### Post by backu on 2011-05-25
I know what you mean. I've been playing around with Jack and IDJC for a little bit now, and managed to get all 6 outputs channels on my soundcard working, plus both inputs, and get my headset (2 out/1in) added in, along with Skype Connectivity.

---

