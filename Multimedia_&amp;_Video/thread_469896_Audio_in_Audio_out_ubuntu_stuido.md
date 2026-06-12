---
title: "Audio in/ Audio out ubuntu stuido"
date: 2007-06-10
forum: Multimedia &amp; Video
---

### Post by ghostandmachine on 2007-06-10
I'm not sure if this post works in the multimedia section, if not please redirect.

got ubuntu studio working and I'm trying to get the input of the microphone to work with programs such as ardour or wired. I've done the alasmixer and bumped up the volume on the mic port. Linux understands my sound card Intel 82801DB-ICH4 but when I go to hit record nothing moves or records. Ardour doesn't even have my sound card as an option when in the settings of audio in/out just says none.

any help would be great. and again if I'm posting in the thread just redirect it please.

thanks in advance
-gam

---

### Post by ghostandmachine on 2007-06-11
bump

---

### Post by duojet on 2007-06-11
Wall, funny thing that alsa mixer is, you could have the MIC up, and be plugged into what it sees as the LINE input, or your ADC volume could be too low, One way to do it is to turn down your speakers, and then just crank everything in alsamix until you get something, even if it's wild feedback. 

But, even if your soundcard isn't correctly set up, the transport in ardour should move. You should at least see the red playback marker scrolling. if you don't see that, you might have a much deeper problem.

You may want to consult the ardour forums, and you might get better help there, as plenty of the experts there use ubuntu

---

