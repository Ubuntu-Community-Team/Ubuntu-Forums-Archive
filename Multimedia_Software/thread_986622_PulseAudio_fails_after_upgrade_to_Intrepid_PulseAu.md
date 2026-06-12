---
title: "PulseAudio fails after upgrade to Intrepid: PulseAudio: Unable to connect:"
date: 2008-11-18
forum: Multimedia Software
---

### Post by felixdzerzhinsky on 2008-11-18
After upgrading to Intrepid my sound stopped working. How do I troubleshoot this?


```
felixdz@gUn:~$ alsamixer
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused


alsamixer: function snd_ctl_open failed for default: Connection refused
felixdz@gUn:~$ 
```

---

### Post by feedmecereal on 2008-11-29
I've been having the very same problem since I upgraded to Intrepid. Have you found a solution yet?

---

### Post by mocha on 2008-11-29
Is pulseaudio running?  Try "pulseaudio -D" then run alsamixer.

---

### Post by feedmecereal on 2008-11-30
danny@danny-desktop:~$ pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: daemon startup failed.
danny@danny-desktop:~$ alsamixer
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection terminated


alsamixer: function snd_ctl_open failed for default: Connection refused

---

### Post by tom17 on 2008-12-03
My pulseaudio works fine after a reboot, but then after some amount of time (hours or days) I get the exact same symptoms.

It's getting on my nerves

---

### Post by psyke83 on 2008-12-03
Ensure you have a valid PulseAudio configuration. See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Fibonacci on 2008-12-04
Same problem here.
Try to kill and then restart pulseaudio. At least it will get you sound until the problem appears again.

---

### Post by blumojo on 2008-12-04
I feel so stupid for the problem that I had, because the solution was so simple (after trying everything for 2 days);

I went to the alsa mixer:
```
alsamixer
```

Navigate to the two "H/W" fields (with the Left/Right arrow keys) and make them read "PCM Out" by pressing the up/down arrow keys on the keyboard.

The same thing can be done in the GNOME volume control if you click Preferences, check everything, & change the H/W fields on the Options tab.


I went through this thread;
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
and several others over the course of the two days, but never saw any mention of this.  

The sound was not coming out of the speakers after I upgraded from an on-board sound card to an Audiophile 2496 card.  I tried some of the live CDs (MusiX, Ubuntu 8.04 install Live CD, Knoppix, etc.) and everything worked, so I knew it had to be in my configuration.

---

