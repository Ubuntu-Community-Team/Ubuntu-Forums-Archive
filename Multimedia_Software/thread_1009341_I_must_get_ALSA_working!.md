---
title: "I must get ALSA working!"
date: 2008-12-12
forum: Multimedia Software
---

### Post by Trifid on 2008-12-12
Right, I have a M-audio 2496 sound card. When I installed Ubuntu 8.10 I had no sound and looking around the best way around it was to use OSS instead which I used this guide for: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

All well and good, but OSS is having problems with crackly sound and only locking the device to one program at a time. Very annoying and I had none of these problems on previous versions on ALSA. 

Selecting ALSA in sound properties causes the following error:

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

The only device is my M-audio 2496 (OSS v4 Audio mixer). I am now at a lost end after trying several things mentioned on this forum. 

Anyone have any ideas?

Thanks.

---

### Post by pseudonym on 2008-12-12
Before doing any more experimenting with ALSA I'd strongly recommend that you uninstall OSS first. From memory it comes with an uninstall script but it's been a while since I used it.

---

### Post by josedb on 2008-12-12
Why dont you use pulseaudio?

---

### Post by Trifid on 2008-12-12
> **josedb said:**
> Why dont you use pulseaudio?

I get the same error as I do with ALSA. The only sound device I have listed in the GUI Sound settings is the M-audio with OSS4 in the title of it. OSS is the only thing that can detect it by the looks of it. 

Sorry if I am being a bit vague but I am a bit lost with the sound now...

---

### Post by Trifid on 2008-12-13
> **pseudonym said:**
> Before doing any more experimenting with ALSA I'd strongly recommend that you uninstall OSS first. From memory it comes with an uninstall script but it's been a while since I used it.

Does anyone know how I can go about doing this? Infact a way to revert to new install sound defaults would probably be good (without a reinstall).

---

### Post by pseudonym on 2008-12-13
> **Trifid said:**
> Does anyone know how I can go about doing this? Infact a way to revert to new install sound defaults would probably be good (without a reinstall). It should be in the documentation that was installed with OSS. Look in eg /usr/share/doc/opensound.

If it's the same setup when I used it (circa 2005) there is a script you run as sudo which removes all the OSS modules and returns your ALSA configuration to what it was before you installed OSS.

---

### Post by Trifid on 2008-12-17
> **pseudonym said:**
> It should be in the documentation that was installed with OSS. Look in eg /usr/share/doc/opensound.

If it's the same setup when I used it (circa 2005) there is a script you run as sudo which removes all the OSS modules and returns your ALSA configuration to what it was before you installed OSS.

I do not have that directory on my installation... I have however tried the guide for removing OSS in the link to install it in the OP and OSS is still working (sounds a little less crackly/popping than before in 16/48KHz music, ALSA is not working and still have the problem applications *locking the sound device to it until it is closed. 

*(If I play a Youtube video in Firefox, I need to close Firefox completely before I can play a track in SongBird.)

Thanks.

---

