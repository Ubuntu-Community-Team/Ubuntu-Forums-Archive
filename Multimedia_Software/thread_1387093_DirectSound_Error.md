---
title: "DirectSound Error"
date: 2010-01-21
forum: Multimedia Software
---

### Post by astroblack on 2010-01-21
I recently installed Steam and Darwinia. I already had Wine installed so the Steam install went pretty quickly. I used [this page]("https://wiki.ubuntu.com/UbuntuMagazine/HowTo/InstallingSteam") to help me install it. In a matter of minutes I had Darwinia installed as well. Although everytime I try to launch the game it gives me [this message]("http://img714.imageshack.us/img714/5742/darwiniaubuntuerror.png").

I thought it might be this
> Getting more than one application to use the soundcard at the same time
You might want to play a game and listen to music on your favorite music player at the same time. To do this successfully, you will have to use ALSA since it supports this feature the best. On all the music players I know of, you can configure the sound engine, to any module that is available.
The setting is usually found under something like Tools >>> Configure >>> Player Engines.
For games, it is a bit more tricky since there is not always a way to configure the player engine directly. Most games, however, do support the OSS. ALSA has an OSS module that allows OSS applications to use the ALSA driver.
To do this you will need the alsa-oss package
Code:
sudo apt-get install alsa-oss
After doing this step, it is very easy to use alsa-oss. In the shell, you can type 'aoss' then the name of the program name you want to use with alsa-oss.
But that did not fix the problem either.

---

### Post by Yellow Pasque on 2010-01-21
Play around with different WINE audio drivers. Maybe Pulse or EsounD driver will work.
```
winecfg
```

---

