---
title: "Sound in Ubuntu suddenly stops - possible solution"
date: 2007-07-20
forum: Multimedia &amp; Video
---

### Post by dhakir on 2007-07-20
I'm using Feisty on my HP NC6000 laptop, and I had never had any sound problems at all (Intel 82801DB-ICH4 sound card), but recently while watching Sun Learning Connection courses, sometimes the sound just stops working after a while. Not just in Firefox, but everywhere (Flash sites, VLC, Ubuntu sound test, etc). I had to reboot to make it come back again, and if I tried checking the settings at System -> Preferences -> Sound, I wouldn't get any results from the Test button (either for Sound Events and Music and Movies). Both are always configured as "autodetect", but after the sudden loss of sound happens, this setting produces no sound at all. During these situations, if I try to manually set the sound playback to my sound card's (Intel 82801DB-ICH4), it would display the following error message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resouce for writing.

I looked for some information on several forums, and none of the suggestions worked.

After this problem happened for the fourth time, I decided running ps and checking whether some process was keeping the sound device "busy", or something like that. Then I found these two processes:

 /bin/sh -c /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 24
 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 24

Since they were related to the Enlightened Sound Daemon and were the only ones which seemed somehow related to sound devices, I tried killing the second one and, after that, sound was working again.

I went to the Sound Preferences again and tested using both "autodetect" and "Intel 82801DB-ICH4" settings, and they worked fine (no more error messages). As expected, trying the ESD setting produces an error message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not establish connection to sound server

Then, I tried running "/bin/sh -c /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 24" in the background and the ESD option would also work.

I couldn't reproduce the error again to do further testing, but I believe that this solution (killing the esd process) could help people having similar problems. I didn't post it as a bug since I don't know the exact cause nor the steps to reproduce it, but maybe someone can have an idea  about why esd "hangs" sometimes, blocking sound events.

---

### Post by tfarinella on 2007-07-20
i have a simular problem my sound works only when it wants to!

what were the exact steps you took???

---

