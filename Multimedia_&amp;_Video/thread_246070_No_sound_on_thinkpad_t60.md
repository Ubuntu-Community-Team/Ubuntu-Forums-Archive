---
title: "No sound on thinkpad t60"
date: 2006-08-28
forum: Multimedia &amp; Video
---

### Post by minchina on 2006-08-28
I just installed kubuntu on my new T60 and I am not getting any sound.  I checked the Kmix and nothing is muted, checked Alsamixer and nothing is muted, and my soundcard is recognized.  Is there some sort of secret hidden mute button that I am missing?

Thanks in advance for any help, and let me know if there is more information that I can pass on.

---

### Post by minchina on 2006-08-29
I also just tried to hook up my USB headset and it works perfectly in skype (the only program that I know how to change the audio output in).  I assume that there is an obvious solution to this that I am overlooking, but I just can't seem to find it.  Please help

---

### Post by minchina on 2006-09-21
Just in case anyone else is having this problem I fixed it.  I changed the sound driver from 'default' to 'ALSA'.  This fixed everything.

---

### Post by dannyboy79 on 2006-09-22
how did you do this? what config file do you change etc etc. Thank you if you can be more specific.

---

### Post by minchina on 2006-09-22
I did not need to edit any config files.  All you have to do is:

K -> system settings -> sound & multimedia (in the first set of icons) -> sound system -> hardware tab.  The first drop down menu asks you to select your audio device.  Change it from 'Autodetect' to 'Adanced Linux Sound Architecture'.  You may have to restart.  It is also worth noting that the thinkpad sound buttons work even though there is no on-screen indication that they are doing so.  Hit the volume up button just to make sure that everything is not muted.  I think that they are going to integrate in screen indications for these buttons into the next release, but for  now as far as I can tell you just have to wing it.

let me know if you need more info on this

---

