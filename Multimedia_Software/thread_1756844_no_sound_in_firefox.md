---
title: "no sound in firefox"
date: 2011-05-12
forum: Multimedia Software
---

### Post by u_kapaley256 on 2011-05-12
Hello all,
         I am using kubuntu 11.04 . Recently sound stopped working on my system except for amarok. I did some digging and got it working for vlc by setting 

Output module : ALSA audio output 
Use S/PDIF when available : checked
Device : HDA ATI SB: STAC92xx Analog (hw:0,0) 

Also , amarok and vlc cannot play sound at the same time.
  
It seems ( from my limited knowledge) here that PulseAudio is broken.

Regardless, how to get sound in firefox ??  

Thanks

---

### Post by lidex on 2011-05-14
Do you have pulse audio installed?
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by u_kapaley256 on 2011-05-21
Thank you so much lidex . That totally worked .

---

### Post by lidex on 2011-05-22
You're welcome ;)
Please mark the thread solved using 'Thread Tools' up top.

---

