---
title: "No audio in Firefox, Chome &amp; Chromium work"
date: 2018-01-04
forum: Multimedia Software
---

### Post by lindend on 2018-01-04
I had to disable pulseaudio to bitstream audio in Kodi and fix some other issues.  I've setup a default ALSA device and Chome, Chromium, vlc and movies etc. are playing fine with the default device (at 48khz).  However, I have no audio in Firefox.  Any suggestions on what I can do to debug/fix this?

On Ubuntu 16.04 LTS

---

### Post by deadflowr on 2018-01-04
Some background for you:
[http://www.omgubuntu.co.uk/2017/03/firefox-52-no-sound-pulseaudio-alsa-linux]("http://www.omgubuntu.co.uk/2017/03/firefox-52-no-sound-pulseaudio-alsa-linux")

---

### Post by lindend on 2018-01-04
Thanks for the link to that thread.  Prior to posting, I noticed the thread but missed a couple key parts.  I originally saw that 

--enable-alsa

compilation option at the start of the thread and thought that's how the FF in the LTS distro was being built.  Am I correct in understanding that FF 55 and up can't be used with ALSA?

---

### Post by Yellow Pasque on 2018-01-05
[https://codelab.wordpress.com/2017/12/11/firefox-drops-alsa-apulse-to-the-rescue/](https://codelab.wordpress.com/2017/12/11/firefox-drops-alsa-apulse-to-the-rescue/)

---

