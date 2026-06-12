---
title: "unplugging issue"
date: 2006-09-15
forum: Multimedia &amp; Video
---

### Post by onlythetim on 2006-09-15
My problem: I was listening to music (with amarok) on my headphones (connected to my laptop), and wanted to play the music from the laptop speakers, so I unplugged the headphones, but no sound came out, amarok said it was still playing.  So I plugged the headphones back in, and music came from the headphones.  I unplugged them again, and no sound.  This time when I plugged them back in, no sound, and I haven't been able to get any speakers, plugged in or built in to work since.

I recently updated my kernel, but I had this problem before I restarted after updating...

My System: Dell latitude D820, intel high definition audio controller

---

### Post by deadgobby on 2006-09-15
MMMM maybe the speakers need to have a power supply source to able to amp the sound? If not try opening up the termimal and type in 
killall esd 
 and see if that restores the sound.
Gobby

---

### Post by onlythetim on 2006-09-15
I noticed that oss works, but alsa does not.

killall esd did not fix the problem...

---

### Post by shat on 2006-09-15
I've had similar problems with headphones before...

Check your home directory with a ls -a and see if there are any sound configuration files, and try moving them to another folder and see if your sound comes back.  Worth a try.  When I plugged in my headphones alsa made some goofy config files to use the headphones as a default device, so when the headphones were disconnected, nothing would play through alsa, just oss.  Getting rid of those config files solves my problem.

Edit:  This was with a USB headset device, and the filenames were somthing like .asoundrc

---

