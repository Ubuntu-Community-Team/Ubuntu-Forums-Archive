---
title: "how to i play a cd in xmms"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by blackmajik2021 on 2007-05-08
ive put a cd in my cd drive but i cant get it to open with anything but the default ripping program. im a huge noob btw i just got ubuntu last night. any help would be appreciated.

---

### Post by mills on 2007-05-08
been trying to figure this out for the last half as i want to be able to do it aswell
i've got as far as getting xmms to open by putting the cd in but cant get it to play

go to system - preferences - removable drives and media - multimedia

i browsed to xmms in /usr/bin and selected xmms, which gets it to open xmms but like i said wont play the cd,

 if anyone knows the right command let us know,

---

### Post by orbister on 2007-05-10
I have just got this working, almost. First I followed the instructions at [http://www.ma.utexas.edu/users/stirling/computergeek/xmms.html](http://www.ma.utexas.edu/users/stirling/computergeek/xmms.html) and installed the xmms-cdread package. Then, as instructed, I disabled the CD plugin which comes with xmms and made sure the new one was enabled.

Next, I went to System->Preferences->Removable drives and media->Multimedia and made the Audio CD action "xmms /dev/cdrom"

This pops up xmms just fine, and pointed at the CD, but I still have to hit "play" to start the noise. "xmms -p /dev/cdrom" doesn't, as I had hoped, autostart.

---

### Post by mills on 2007-05-10
Orbister    ==  legend

but you forgot to tell me to reboot:P :guitar:

---

### Post by monkey4ahead on 2007-05-14
I have "xmms --play /media/cdrom" in my System->Preferences->Removable drives and media->Multimedia and it autoplays.

---

