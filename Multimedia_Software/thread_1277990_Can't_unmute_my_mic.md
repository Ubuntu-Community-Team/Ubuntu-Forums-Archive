---
title: "Can't unmute my mic"
date: 2009-09-29
forum: Multimedia Software
---

### Post by Sourien on 2009-09-29
Ok, so I'm almost certain that I saw something about this before, when I didn't need it but now it seems like it's nowhere to be found.  Anyway, my mic was working earlier, but now I get nothing.  This was immediately after tinkering with my sound preferences.  I had everything under the devices tab set to pulseaudio(except for the mixer, which was alsa), then tried switching to Alsa to see how it worked.  After I did this, I noticed that in volume control, under the recording tab, the capture and digital both were muted.  I tried unmuting them, but they just show as being muted every time I open volume control.  I tried returning to pulseaudio, but to no avail.  By the way, I'm using ubuntu 9.04.  I'm pretty new to linux so dumbed down talk is very appreciated.  If you need more details, please tell me how to get said details.  Any help at all is appreciated and thank you in advance.

---

### Post by Remmo87 on 2009-10-25
I have the very same problem.....
Ive tried everything with the sound options and settings... im
Tested it both with skype, messenger and sound recorder because i heard from someone that it unmutes itself when used. but its not true in my case.
Whenever i go to Volume Control, the capture is always muted.

Ubuntu team ive seen so many threads with this problem not being fixed.

---

### Post by BatsotO on 2009-11-07
this is not the fix, but you can unmute mic via gnome alsa mixer

sudo apt-get install gnome-alsamixer

---

### Post by Jazzy_Jeff on 2009-11-07
The mic and capture are supposed to be muted. If it will not record then click on the options tab under the volume control and make sure the input source says mic. If it does change it to something else and then back. If there is no options tab then click on the Preferences button on the bottom and check the mic. Also check the mic boost.

For some reason every time I restart my system I have to go back in and change the input source from mic to something else and back to mic for it to start working. Not sure what causes this. Hope this helps.

---

### Post by BatsotO on 2009-11-07
pulseaudio did

---

