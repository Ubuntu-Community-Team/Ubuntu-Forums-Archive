---
title: "Video problem"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by Zacharias on 2007-05-08
even i have already installed all codec packages, i heard sounds but cant watch :(

how can i fix that problem ?

---

### Post by blackened on 2007-05-08
What file format are you trying to view and with what player?

---

### Post by Zacharias on 2007-05-08
avi, mpeg, mov i try to view different formats

---

### Post by taurus on 2007-05-08
And how did you install the codec package?  Which release are you running right now?

---

### Post by Zacharias on 2007-05-08
7.04 is my realized
i installed the these packages.

sudo apt-get install gstreamer0.10-ffmpeg
sudo apt-get install gstreamer0.10-plugins-base
sudo apt-get install gstreamer0.10-plugins-good
sudo apt-get install gstreamer0.10-plugins-ugly
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
sudo apt-get install gstreamer0.10-fluendo-mp3
sudo apt-get install gstreamer0.10-fluendo-mpegdemux
sudo apt-get install gstreamer0.10-plugins-bad-multiverse
sudo apt-get install gstreamer0.10-plugins-bad
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-plugins-multiverse
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install mplayer-386
sudo apt-get install mozilla-mplayer
sudo apt-get install mplayer-fonts
sudo apt-get install mplayer-skins

i hear the sound but cant watch

---

### Post by taurus on 2007-05-08
Have you tried vlc media player?

---

### Post by Zacharias on 2007-05-08
no i havent

---

### Post by Zacharias on 2007-05-08
i have already installed the vlc from synaptic still i hear sounds but cant watch :(

---

### Post by Zacharias on 2007-05-09
any suggestion?

---

### Post by Nythain on 2007-05-09
> **Zacharias said:**
> 7.04 is my realized
i installed the these packages.

sudo apt-get install gstreamer0.10-ffmpeg
sudo apt-get install gstreamer0.10-plugins-base
sudo apt-get install gstreamer0.10-plugins-good
sudo apt-get install gstreamer0.10-plugins-ugly
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
sudo apt-get install gstreamer0.10-fluendo-mp3
sudo apt-get install gstreamer0.10-fluendo-mpegdemux
sudo apt-get install gstreamer0.10-plugins-bad-multiverse
sudo apt-get install gstreamer0.10-plugins-bad
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-plugins-multiverse
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install mplayer-386
sudo apt-get install mozilla-mplayer
sudo apt-get install mplayer-fonts
sudo apt-get install mplayer-skins

i hear the sound but cant watch
none of those are codecs really, just plugins and whatnot... you need the w32codecs package from medibuntu more than likely
first you need to add the gpg key
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```
then add the repo to your /etc/apt/sources.list:
```
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```
then
sudo apt-get update
sudo apt-get install w32codecs
that should help you out

---

### Post by Zacharias on 2007-05-09
[http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

site is not working now... which depos should i add my sources.list

---

### Post by Zacharias on 2007-05-09
it is very interesting and boring although i have already installed win32codecs still only hearing sounds cant watching... 

please help 

graphic card is ATI x800

---

