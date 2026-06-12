---
title: "sound stopped working I think I tried everything"
date: 2009-12-20
forum: Multimedia Software
---

### Post by Reliam on 2009-12-20
OS: Ubuntu 9.10  Minimal Install/Openbox

For some reason my sound just stopped working. 
I have tried reinstalling all the sound packages. 
I have tried --purge remove all and reinstalling them 
I have tried the Alsa Script from here [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

What is weird is before I startx alsamixer starts and aplay-l displays my cards but once started the terminal gives me errors until I sudo the commands  

I tried "sudo adduser  sound" but I get the error that the sound group does not exist. 
I tried adding a sound group with groupadd then adding myself to it but still a no go  


!!! pulling my hair out


Edit: Seems its not sound group its audio group... I added myself to that and the commands are working but before I did that I updated the script to include the lastest packages and now my damn card is no longer listed !!!

Edit2: Tried the alsa-base.conf fix and nothing... Alsamixter states " This sound device does not have any controls" and aplay -l states "**** List of PLAYBACK Hardware Devices ****"

Edit3: aplay stats 
"ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
aplay: main:608: audio open error: No such file or directory"

---

