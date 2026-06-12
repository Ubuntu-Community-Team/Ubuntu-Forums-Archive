---
title: "No playback from line-in"
date: 2009-01-29
forum: Multimedia Software
---

### Post by DrVitoti on 2009-01-29
I have a CMI9880 sound card, and when I plug a line-in input it does not produce any sound on my speakers. Everything else works fine, I can record, I can listen to audio files, but cannot hear what I record (monitoring). I have tried "playing" with the sound control manager, but it just doesn't work. In fact, I have seen more people with the same problem, and no answer. I would really appreciate it if you could help me.

---

### Post by markbuntu on 2009-01-29
I am not familiar with that card but other CMI cards use the line in for some surround sound output. This is switchable in the volume control/options.

---

### Post by DrVitoti on 2009-01-29
I can actually record well, but it's like i f I could not connect the recording and the speakers.

With audacity I record the sound from the Xbox 360 (which is the thing I want to hear), but I cannot make audacity emit any sound, I know it is recordered because I can see the lines going up and down, I mean, its not a straight ine, you can see it is recorded, so the recording works well, and I can also play music with Songbird, so it is not the speakers or anything related. I've really looked for the solution in any possible place and no one has an answer, I'm starting to think it's an Ubuntu bug. It's not about the version either because it didn't work in Hardy and still doesn't work on Intrepid.
If anyone solves this, he/she will be my hero:p, I've been with this issue for too long.

---

### Post by markbuntu on 2009-01-29
The problem is with audacity and its buggy alsa and pulseaudio plugins. The audacity devs are the only ones who can fix it.

---

### Post by DrVitoti on 2009-01-30
But, theoretically, I shouldn't need to use audacity to monitor the line-in input, Ubuntu should make it work, but it does not. Another thing that I have noticed is that every time I open volume control, the microphone icon below the slides Capture 1 and 2 and Digital appear with a cross on it, if I click on the microphones the cross disappears, but if I close volume control and open it again, the cross is back there. Plus, I have read that to control the monitoring option, there's a slide called analog mix, well, I don't have that slide, I have checked in Preferences, I have it all ticked, but it does not appear (yeah, I've tried with all the devices available).

And the audacity thing, it first worked, but somehow it stopped working the next time I opened it.

---

### Post by DrVitoti on 2009-01-30
I got audacity working now, but I cannot make it work without a program (I want it to work just with the OS, like in Windows when you click "Monitor 1" and just plays what your recording). By the way, on alsa mixer, I only have 2 slides, Master and Capture. I've read that normally you have many more, so, could this be the problem? How can I solve it?

Thanks for your time.

---

### Post by markbuntu on 2009-01-30
There is a big long sound troubleshooting guide here


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by DrVitoti on 2009-01-31
I have alreday read it, I cannot fix the problem. I am pretty sure it is something related to not having all the sliders I am supposed to have in ALSA mixer.

---

### Post by markbuntu on 2009-02-01
How are you accessing the alsa mixer?
If it is from the panel then many controls are hidden and must be enabled in Preferences.

---

