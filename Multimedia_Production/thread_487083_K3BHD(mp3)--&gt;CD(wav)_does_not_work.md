---
title: "K3B:HD(mp3)--&gt;CD(wav) does not work"
date: 2007-06-28
forum: Multimedia Production
---

### Post by steveM49 on 2007-06-28
I would like to use Kubuntu (Feisty Fawn) for all my music.  K3B looks like a great application and the documentation says that it will produce a playable CD from mp3 files.

But it doesn't.  It says that it cannot do the conversion from mp3 to wav.  This looks like a silly error caused by linking to the wrong library.

Can anyone help me correct it?

Thanks
Steve

---

### Post by daschmidty on 2007-06-28
```
sudo apt-get install libmad0 libk3b2-mp3
```

---

### Post by steveM49 on 2007-06-28
I reinstalled those libraries using Synaptic.  When I tried to create a music CD again, I got:

Unable to handle the following files due to an unsupported format:
You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project.

It does not seem to be working. 

Steve

---

### Post by arizonagroovejet on 2007-09-23
I have the same problem. libk3b2-mp3 and 'K3b MAD decoder' is listed in the Plugins section of the configuration but still K3b tells me 'unsupported format'. It's quite infuriating.

---

### Post by UbuWu on 2007-09-23
Brasero does that with no problems (although it is a gnome application, you can install it in kubuntu as well)..

---

### Post by craftbrewer on 2007-11-18
so is there an actual fix to this problem yet?    why do i need to dick around with lib pointers everytime there's a new release of ubuntu ?

---

### Post by steveM49 on 2007-11-19
> **craftbrewer said:**
> so is there an actual fix to this problem yet?    why do i need to dick around with lib pointers everytime there's a new release of ubuntu ?

It wasn't that difficult for me.  Eventually, I tried using the app with a different user name.  Everything was fine.  I suppose the problem lay in the user settings.

Steve

---

### Post by BLTicklemonster on 2008-01-12
I have the same problem 
Installed brasero  sudo aptitude install brasero

Wow, nice. Thanks!

---

### Post by eye208 on 2008-01-14
> **craftbrewer said:**
> why do i need to dick around with lib pointers everytime there's a new release of ubuntu ?
I guess you mean _K_ubuntu.

---

### Post by Huss on 2008-03-13
Brasero worked for me. Thanks!

---

