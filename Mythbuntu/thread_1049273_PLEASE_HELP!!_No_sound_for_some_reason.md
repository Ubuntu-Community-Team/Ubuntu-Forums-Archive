---
title: "PLEASE HELP!! No sound for some reason"
date: 2009-01-24
forum: Mythbuntu
---

### Post by Hal_Emmerich on 2009-01-24
Heya. Heres a strange one. Please help because my uncle just died this morning and, after everything else this week, not being able to get this working would just be the icing on the cake.

Everything appeared to be working well after the install. Things were configured, working. It was playing sound from videos perfect and we watched something on it.

The computer was shut down, and powered on this morning to get an ATI remote to work. 

It no longer has sound.

I can recount the exact steps that have been taken since it was working, but none of them add up to anything that should have affected it. 

#1: Used Terminal to launch Thunar in Root user
#2: Added ati_remote to blacklist in /etc/modprobe.d/
#3: Overwrote the LIRC.d and ~/.lirc/mythtv to my own configuration
#4: Restarted LIRC and used IRW to test the remote
#5: Restarted Mythbuntu
#6: Tried to play a movie, but got no audio

This makes no sense, and its happened before. Every time, I reinstall mythbuntu to fix the problem. The audio works until I start working in root for some reason, then the audio stops working and I never get it working again.

Please help!

---

### Post by Hal_Emmerich on 2009-01-24
Probably should give more info, huh?

Its an Ensoniq PCI audio card, rather than using whatever is onboard.

---

### Post by khelben1979 on 2009-01-24
From my short experience by using Ubuntu, everytime a newer kernel is installed (which happens through usual updates) the ALSA stops working.

The ALSA system then needs to be reconfigured or reinstalled to start working again.

Take a look [at this thread]("http://ubuntuforums.org/showthread.php?t=1028012"), maybe it can help you?

But before you start doing what is described above, take a look at your sound settings in alsamixer.

---

### Post by Hal_Emmerich on 2009-01-24
Restarting the card through Alsa-utils worked, actually. Thank you so much for the idea.

---

