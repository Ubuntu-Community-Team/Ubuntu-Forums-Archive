---
title: "mp3 problems in Natty"
date: 2011-09-16
forum: Multimedia Software
---

### Post by jason7537 on 2011-09-16
I have spent weeks reading through every post I can find and trying every different codec I can find but nothing will allow me to play mp3 files.  I am somewhat new to Ubuntu but I can usually get things to work by just searching and finding out what people have already done but nothing seems to be working.

when I try opening an mp3 with the standard media player it says there is no suitable plugin.  If I click search it tells me "No packages with the requested plugins found.... the requested plugins are: MPEG-1 Layer 3 (MPR) decoder"

Also I am running 64bit

Any help would is greatly appreciated. Thanks!

---

### Post by dniMretsaM on 2011-09-16
Do you have the restricted extras installed? If your on Ubuntu:
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

Kubuntu:
```
sudo apt-get update
sudo apt-get install kubuntu-restricted-extras
```

Xubuntu:
```
sudo apt-get update
sudo apt-get install xbuntu-restricted-extras
```

Lubuntu;
```
sudo apt-get update
sudo apt-get install lubuntu-restricted-extras
```

---

### Post by jason7537 on 2011-09-16
Yes I tried that as well as many other codecs.  I'm running Ubuntu 64 bit, but thanks for posting all the other possibilities as well.

---

### Post by dniMretsaM on 2011-09-16
What codecs and what converters? Have you tried getting audio in another format, converting it with, say, FFmpeg, and then playing it? It's possible that it's a 64 bit problem. Are you sure you're installing 64 bit software? And just curious but why don't you use another media format? Ogg Vorbis is higher quality (much higher a lower bitrates), it has a higher compression, and is more computationally efficient.

---

### Post by varunendra on 2011-09-17
> **dniMretsaM said:**
> ....just curious but why don't you use another media format? Ogg Vorbis is higher quality (much higher a lower bitrates), it has a higher compression, and is more computationally efficient.
While what you are saying is true (as with aac), the mp3 format is so widespread that practically it is not possible currently to do away with it if we wish to listen downloaded music or view downloaded videos. It's (unfortunately) everywhere.

@jason7537,

Do you have gstreamer plugins installed? Open synaptic package manager (under "System Settings" in natty) then goto its Settings > Repositories make sure 'Universe and 'multiverse' are checked > close the settings > reload > then either retry to open the mp3 file and install the plugin from within the player, or install it manually from synaptic. There should be many in the list, gstreamer ffmpeg is what I think you need.

You can also try installing VLC player (in the repo) which itself is a very good player, and should install all the required plugins automatically.

---

### Post by dniMretsaM on 2011-09-17
> **varunendra said:**
> While what you are saying is true (as with aac), the mp3 format is so widespread that practically it is not possible currently to do away with it if we wish to listen downloaded music or view downloaded videos. It's (unfortunately) everywhere.

True, but I personally don't use anything on my computer except Ogg Vorbis. So it is possible. But yes, it is everywhere.

---

### Post by andrew.46 on 2011-09-17
> **dniMretsaM said:**
> True, but I personally don't use anything on my computer except Ogg Vorbis.

Another vote here for Ogg Vorbis, great sound, some excellent tools to manipulate the files and no encumbrances of license or patent....

---

### Post by dniMretsaM on 2011-09-17
> **varunendra said:**
> Do you have gstreamer plugins installed? Open synaptic package manager (under "System Settings" in natty) then goto its Settings > Repositories make sure 'Universe and 'multiverse' are checked > close the settings > reload > then either retry to open the mp3 file and install the plugin from within the player, or install it manually from synaptic. There should be many in the list, gstreamer ffmpeg is what I think you need.

If he has the restricted extras installed, he has the gstreamer plug-ins.

---

### Post by jason7537 on 2011-09-19
I have actually been having allot of problems with Ubuntu since I reinstalled with a dual boot.  I used a backup program called simple backup suite which im pretty sure messed allot of things up, so I going to do a new installation.  I never had very much trouble at all before this and now it seems like I'm getting a completely different error every day. Thanks for the help though.

---

