---
title: "Problem Playing Mp3 Files"
date: 2008-08-07
forum: Multimedia Software
---

### Post by trebllaw on 2008-08-07
Hi.. I have a problem playing mp3 files.. It is stored on a NTFS Partition on my portable hard drive.. Everytime i play it using Amarok, it says audio output is busy.. tried playing it on rhythmbox, helix, exaile, audacious but it cannot play it.. only VLC plays the mp3 file.. 

Does anyone know how to correct this problem?

---

### Post by fuzzyk.k on 2008-08-07
do you have codecs installed ?

---

### Post by jualin on 2008-08-07
Are you using Ubuntu or Kubuntu?

---

### Post by jualin on 2008-08-07
In Ubuntu the problem can be fix by going to System, Preferences, Sound and changing everything ot ALSA. Then you will need to go to Amarok and change the output plugin there. You can do that by going to Settings, Configure Amarok, Engine, and then change the output plugin to ALSA

---

### Post by jualin on 2008-08-07
> **fuzzyk.k said:**
> do you have codecs installed ?

And for the codecs, try installing ubuntu-restricted-extras **or** kubuntu-restricted-extras using Synaptic Package Manager, Adept Package Manager, or the terminal > sudo apt-get install ubuntu-restricted-extras or > sudo apt-get install kubuntu-restricted-extras
Hope this helps!

---

### Post by prshah on 2008-08-07
> **trebllaw said:**
>  Everytime i play it using Amarok, it says audio output is busy.. 

If you're using ALSA, you can have sound from only one application at a time. If any other application is using sound (Browser, Video, etc) then a newly opened program will not have access to sound.

To get around this, setup pulseaudio on your system. You can get more information from this forum thread:
[HOWTO: PulseAudio Fixes & System-Wide Equalizer Support (Hardy Heron)]("http://ubuntuforums.org/showthread.php?t=789578")

---

