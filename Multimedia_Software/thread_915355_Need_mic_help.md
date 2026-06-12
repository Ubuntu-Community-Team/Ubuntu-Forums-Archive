---
title: "Need mic help"
date: 2008-09-09
forum: Multimedia Software
---

### Post by blakkinferno on 2008-09-09
So I have a cheap little mic that I need for skype and recording things with audacity but I have no input. When i try to record with sound-recorder, it wont open because "Your audo capture settings rae invalid. Please correct them in the Mutlimedia settings." Audacity gives a different error, that says "Error while opening sound device. Pleas echeck the input device settings and the project sample rate." So, I need your help, what do I need to edit? I checked alsamixer and made sure the mic volume was all the way up, and checked some box called stereo mic, but I don't know what I need to do to fix this problem.

Help is appreciated, thanks :)

---

### Post by fauzie on 2008-09-14
Could you hear the sound from the mic going thru your speaker? If not then it is a hardware / driver problem.

If yes, then make sure the configs are correct
In alsa mixer, go to recording Tab, make sure both Master record and Mic record is set to record (press Space).

With Audacity, try o install Jack Control and set Audacity recording device to jack.

---

### Post by fauzie on 2008-09-14
Could you hear the sound from the mic going thru your speaker? If not then it is a hardware / driver problem.

If yes, then make sure the configs are correct
In alsa mixer, go to recording Tab, make sure both Master record and Mic record is set to record (press Space).

With Audacity, try o install Jack Control and set Audacity playback and recording device to jack.

---

### Post by skullmunky on 2008-09-16
look in the audacity preferences, in the audio I/O.  try different options for the sound driver for recording.

---

