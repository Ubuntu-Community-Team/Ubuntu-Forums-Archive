---
title: "How do I end audio stutter and disable interruptions?"
date: 2009-03-29
forum: Multimedia Software
---

### Post by Monona on 2009-03-29
I've basically got three questions here:

1. I have multiple logins on my computer, and I use one primarily for audio production, usually while browsing in Firefox.  How can I stop the package manager from occasionally trying to check upgrades, etc., and what other programs run automatically but aren't essential?  I'd like to prevent unnecessary use of system resources when I'm logged in as the audio user.

2. How can I prevent music from stuttering when I'm doing other things, like browsing the web?  I'm talking mostly about audio playback, whether through Rhythmbox, Amarok, or streaming off the web.  Can I give these programs some sort of uninterruptable status? 

3. Also, how can I do this with audio streaming from the internet?  I use Firefox with NoScript and Adblock and some other plugins.  I listen to a lot of internet radio, and I'd like to keep it from stuttering when I'm loading new pages.  Are there any good plugins or ways to give audio priority in Firefox, similarly to above?

---

### Post by markbuntu on 2009-03-29
We need some more details before we can help you, like
What version of Ubuntu are you using?
Are you using pulseaudio?
What hardware do you have?

---

### Post by Monona on 2009-03-29
I'm using Ubuntu 8.04, kernel 2.6.24-23-rt, Gnome 2.22.3.

I don't think I'm using pulseaudio.  Everything in System>Preferences>Sound is set to ALSA, and I use qjackctl when I'm messing around with audio programs.  Would using pulseaudio make things play together nicely?

I have an 1.6GHz Pentium M processor and 483.5 MiB of memory.  I think my sound card is an 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller.  At least, that's what comes up when I run lshw.

---

### Post by markbuntu on 2009-03-30
Here are some links for setting up jack that may be helpful


[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

You are most likely using pulseaudio when jack is not running so getting pulse set up properly might help. This thread can help you get pulse set up and get pulse and jack to work together.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Your machine is at the low end of possibility for running Ubuntu and jack so if you try not to run too many apps at once you may get better results. If you are using destop effects you might want to tunr them off.

---

