---
title: "microphone not working"
date: 2006-09-07
forum: Multimedia &amp; Video
---

### Post by cybertoast on 2006-09-07
i got skype to recognize the mic and it works great. but sound-recorder, and audacity do not receive any input from the mic at all. the alsamixer settings must be good, since skype is using them with no problem. i've got an acer 360, with built in audio, so the system uses /dev/dsp. i've tried:
* arecord test.wav : no luck
* cp /dev/dsp test.wav : no luck
* recording with audacity : no change to the input level (i flatline)
* sound-recorder : recording captures nothing over the microphone.

i don't understand why skype is able to tap the mic, but others are not. is there some codec that should be installed? also, skype is NOT running when i try to record using audacity/sound-recorder

thanks

---

### Post by cybertoast on 2006-09-07
Forget about this thread - a similar discussion is taking place at [http://ubuntuforums.org/showthread.php?t=155571](http://ubuntuforums.org/showthread.php?t=155571) - for some reason i did not notice it when i initially searched for my problem!

---

