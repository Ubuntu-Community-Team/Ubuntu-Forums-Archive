---
title: "ALSA Audio stopped working in 9.04"
date: 2009-06-09
forum: Multimedia Software
---

### Post by JonDubya on 2009-06-09
Running 2.6.28.11-generic kernel & alsa 1.0.20 (manual compile) on Kubuntu 9.04.  HDA Intel, AD198x Digital (IEC958 (S/PDIF) Digital Audio Output); I am using the S/PDIF.

Everything worked fine until I installed some bug & security updates for what I thought were non-related (to audio/alsa).  After a reboot, I could only get analog audio to play normally.  To get digital audio to play I had to play analog audio and then play the digital audio (play the movie) while the analog was playing.  However, if I paused the movie w/ digital playback, I would have to repeat the process to get the audio back.

Then I decided to reinstall gstreamer0.10-alsa; no help.  Then I reinstalled alsa-base (to switch back to 1.18) but after a reboot it still shows v1.20.

So now I'm stuck with only system sounds playing (bootup & shutdown), gmplayer gives the [AO_ALSA] Unable to find simple control 'PCM',0 error.  And a check in alsamixer shows the card and chip as PulseAudio.

I think I need to blow away the alsa 1.20 but don't know how to do that...suggestions?

---

### Post by markbuntu on 2009-06-09
If you are using pulseaudio with KDE4 you should read this. 

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

You also might want to upgrade to pulse0.9.15 which will make controlling the digital outputs easier. There is a PPA  for pulseaudio 0.9.15 here

[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)

---

