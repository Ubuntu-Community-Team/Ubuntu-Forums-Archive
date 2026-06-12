---
title: "Problems with sound"
date: 2012-02-06
forum: Multimedia Software
---

### Post by petrgojda on 2012-02-06
I have just installed Xubuntu 11.10 on my ASUS 6000VM and have problems with sound.
If I put headphones or speakers, no sound comes out ever. And if I try to open the sound settings, I cant edit anything and cant install any driver, as the OS aparently doesnt see the sound card...(and there is also no driver for ASUS and LINUX available on the net).
Is there a way to make the sound card work under Xubuntu? For instance installing some generic driver? And how?
Thanks!!!

---

### Post by MoreOrLess on 2012-02-06
More info please: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by petrgojda on 2012-02-06
Got this, and dont really know what to do with all the infos:-/ Can you help?
Your ALSA information is located at [http://www.alsa-project.org/db/?f=de24247f0f66c85679318175501b96ee9cfc89c4](http://www.alsa-project.org/db/?f=de24247f0f66c85679318175501b96ee9cfc89c4)
thx

---

### Post by MoreOrLess on 2012-02-06
I would try adding this to /etc/modprobe.d/alsa-base.conf
```
options snd-hda-intel model=asus
```

---

### Post by mörgæs on 2012-02-07
Posting the same questions repeatedly is not welcome. I have closed your two other threads.

---

### Post by petrgojda on 2012-02-08
To More or Less.
But adding how and where? Sorry, absolute beginner...

---

### Post by petrgojda on 2012-02-08
To Morgaes: Sorry, beginner at the forum, too. Did write before properly thinking.

---

### Post by petrgojda on 2012-02-10
Ok. Better. I tried your suggestion and now I can set up the sound card (the volume of center, micro etc), the microphone also works under some applications, but the problem when connecting speakers is still tha same:-/

---

### Post by mörgæs on 2012-02-10
Moved to the multimedia forum.

---

