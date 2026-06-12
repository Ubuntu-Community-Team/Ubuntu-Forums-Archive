---
title: "DivX and other video formats assistance NEEDED"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by Dod_basim on 2007-05-26
Hello, I'm a new ubuntuair and very happy for that. but i have problem with playing videos
I'm failing to find a proper AV player that will fit to my need.
My modest needs:
A) play MPEG (all vers) , WMV(all vers) , DivX (avi and all) 
B) play DVD / VCD

What is the problem? i can play most of them with most of the player, i tried Totem, Mplayer, Vlc, democracy  TV. xine. i know it's a problem with codecs usually but nevertheless i couldn't find a proper player.

what should i do? help is needed, thanks!

---

### Post by fenian on 2007-05-26
The answers to all your problems is [here.]("https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restrictedformats%29")

---

### Post by RomeReactor on 2007-05-26
Hi. In my experience, totem-xine with all the required libraries plays every format I throw at it: avi, mpg, wmv, mkv, mp4, mov, ogg, flv, mp3, etc. Totem-gstreamer will most likely cause you problems with DVD playback, so go for totem-xine; the quickest way to install the necessary libraries is to do it from the terminal (Applications-->Accessories-->Terminal). First you need the Medibuntu repositories, if you don't have them:
```
gksudo gedit /etc/apt/sources.list
```
If you're using Feisty then add the following lines at the end of the file:
```
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```
Save the file, close Gedit, and still from the terminal:
```
sudo apt-get update
```
afterwards:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs mplayer w32codecs libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3
```
After the libraries finish their installation, you should be able to play pretty much everything in Totem (including DVD's), and for the one or two files it doesn't play, there's Mplayer.

---

### Post by Nythain on 2007-05-26
im a kaffeine man myself... sounds like you are having more codec issues instead of player issues though because all of those players can play everything on my machine

---

### Post by Dod_basim on 2007-05-27
thanks!!!

i will try to combine all of answers listed!

have a nice day

---

### Post by ib80 on 2007-07-07
Thx RomeReactor for your post. It helped me fix my DVD playback problem in Kaffine/Xine.
All I need now is my popcorn so that the movie night can begin :popcorn: .

Edit : Nice avatar by the way!

---

