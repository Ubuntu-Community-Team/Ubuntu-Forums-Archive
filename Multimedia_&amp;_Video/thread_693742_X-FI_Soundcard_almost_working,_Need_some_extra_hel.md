---
title: "X-FI Soundcard almost working, Need some extra help."
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by rotry on 2008-02-11
Hello everyone, I decided to finally make the leap from Vista to Ubuntu and it has been a great experience. The only setback so far is getting my X-Fi Xtreme music card to work. I have followed many methods to install it, finally manually doing it myself was the solution. I  am using the OSS drivers from 4front technologies. When i issue soundon i get

```
roberto@roberto-desktop:~$ sudo soundon
[sudo] password for roberto:
Detected Creative SB X-Fi *EARLY BETA*
Detected Generic USB audio device (BETA)
Detected OSS Virtual mixer/synth driver
Relinking OSS kernel modules for "2.6.22-14-generic SMP mod_unload 586 "
This may take few moments - please stand by...
Relinking OSS kernel modules finished

OSS started OK

```

which looks good since my card is being detected. after that i can issue ossmixer and i get

```
roberto@roberto-desktop:~$ sudo ossdetect -v
Detected Creative SB X-Fi *EARLY BETA*
Detected Generic USB audio device (BETA)
Detected OSS Transparent Virtual Mixing Architecture

```

which is also encouraging, but i get no sound from any application. My sound options are all set for OSS and when i try to hit the test button i get the message: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

I think thats also the info I have. Thanks in advance guys.

---

### Post by NullHead on 2008-02-12
Well this seems to be the issue with installing OSS (from my own experience). To further test your sound try installing xmms and setting the sound server to "oss".

Also use [this guide ]("http://ubuntuforums.org/showthread.php?t=694029"). Skip past the part that explains the setup of the actual OSS driver( you already have it installed). The guide should get your sound applet working with gstreamer correctly. 

Please post the output of ```
ossinfo
```

Thanks, NullHead

---

