---
title: "Various sound issues"
date: 2009-11-06
forum: Multimedia Software
---

### Post by erikla2002 on 2009-11-06
I installed 9,10 alpha6 or so and have had sound problems all the time since. I have updated everything in Update Manger so far so I guess I can say I am running 9.10. 

I can play sounds and skype works etc but it seems like the audio sources are interrupting each other. If I play a song with VLC or Movieplayer and I get an icoming chat message in skype the sound from skype makes the music in vlc stop for a few seconds. I also get a crackling sound in the speaker just before the "real" sound plays. Rather hard to describe...

I don't get sound at all in Wine if some other application is playing something. 

I tried the alsa upgrade script I found on this forum but it didn't help. Any ideas? I use the integrated sound card on my Gigabyte motherboard so it's a very common sound card.  

Can I completely reinstall alsa/pulseaudio?

---

### Post by kostkon on 2009-11-06
What version of Skype are you using?

The latest beta works fine with PulseAudio so if you have the version of Skype from the Medibuntu repo, remove it, and then go to Skype's website to download the deb for the new beta.

Hope that helps somehow.

---

### Post by erikla2002 on 2009-11-06
> **kostkon said:**
> What version of Skype are you using?

The latest beta works fine with PulseAudio so if you have the version of Skype from the Medibuntu repo, remove it, and then go to Skype's website to download the deb for the new beta.

Hope that helps somehow.


I have the latest skype version. This is not really a skype issue.

---

### Post by erikla2002 on 2009-11-07
Ok I fixed the crackling sound by following this in some other thread:
[http://ubuntuforums.org/showthread.php?t=1310479](http://ubuntuforums.org/showthread.php?t=1310479)

Basically you need to modify /etc/modprobe.d/alsa-base.conf,
changing power_save=10 to power_save=0

But I still have problems with only one application being able to play sound at a certain time.

---

