---
title: "Configuring VLC to use ALSA/Multiple applications using the audio device"
date: 2008-08-04
forum: Multimedia Software
---

### Post by sharad.sharma on 2008-08-04
I recently switched from WindowsXP to Ubuntu 8.04 for my first Linux experience.

I wasn't being able to play audio on two applications simultaneously with the Error : Audio device busy (in Amarok) or simply there was no sound while using other applications.

So,as suggested in the thread, Comprehensive Sound Problem Solutions Guide , I configured most applications to use ALSA as well changed Sound playback in System->Preferences->Sound to ALSA.

I haven't been able to configure VLC to use ALSA and when I use VLC,there is no sound for other applications (eg Pidgin Messenger).What do I do? Please help.

Why does this problem occur?
Is there any other way to allow multiple applications to use the audio device at the same time ,apart from setting each application to use ALSA.

---

### Post by mc4man on 2008-08-04
> I haven't been able to configure VLC to use ALSA 
settings -> preferences -> ck.  advanced options -> expand audio -> highlight output modules and in drop down on right pick alsa

edit 
make sure you _click save_
for future use - highlight interface and ck. show advanced options, then you woun't need to do every time

---

### Post by sharad.sharma on 2008-08-07
Thanks mc4man.. I did that but the problem persisted.

Eventually [the guide here]("http://ubuntuforums.org/showthread.php?t=843012") solved it!

---

### Post by rakusson on 2008-09-09
thanks.

---

