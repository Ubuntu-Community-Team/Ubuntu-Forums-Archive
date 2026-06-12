---
title: "Steps Needed for Amarok To Play WMA files"
date: 2010-09-16
forum: Multimedia Software
---

### Post by cmnorton on 2010-09-16
What do I need to download and from where to play .wma files in Amarok?
Thanks.

---

### Post by mc4man on 2010-09-16
for all wma except wmal (lossless) just install libxine1-ffmpeg
```
sudo apt-get install libxine1-ffmpeg
```
If on a 32 bit install, to add wmal support install w32codecs from here

[http://packages.medibuntu.org/lucid/w32codecs.html](http://packages.medibuntu.org/lucid/w32codecs.html)

---

### Post by cmnorton on 2010-09-17
Thanks. I am already at the latest version:

<code>[sudo] password for cnorton: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxine1-ffmpeg is already the newest version.
The following packages were automatically installed and are no longer required:
  sdparm
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
</code>

I did autoremove, thinking that might be part of the problem, re-tried one of the wma files and got the same behavior.

What else can I try?
tnx

---

### Post by mc4man on 2010-09-17
> What else can I try?
Find out what type of wma the files are and if they are protected.
If they are protected then there's nothing to be done.
If they are wmal and you're on a 64 bit install then very little will play (only a 32 bit mplayer install

Mediainfo can provide info - available thru this ppa
[https://launchpad.net/~shiki/+archive/mediainfo](https://launchpad.net/~shiki/+archive/mediainfo)

So can ffmpeg and or mplayer
ffmpeg -i /path/to/whatever.wma
mplayer /path/to/whatever.wma

Try a wma in another player - gstreamer apps can play wma2, if on lucid the ppa in my sig will add wmas (voice) and wma3(pro) support

Edit 
a couple of views of mediainfo - 1st in 'easy' (wmal). 2nd in html (wma3pro

---

### Post by cmnorton on 2010-09-17
I think you hit it with 64-bit. These came from a 32-bit Windows system. 

How would I find out if they're protected? 

These played on Media Player.
tnx

> **mc4man said:**
> Find out what type of wma the files are and if they are protected.
If they are protected then there's nothing to be done.
If they are wmal and you're on a 64 bit install then very little will play (only a 32 bit mplayer install

Mediainfo can provide info - available thru this ppa
[https://launchpad.net/~shiki/+archive/mediainfo]("https://launchpad.net/%7Eshiki/+archive/mediainfo")

So can ffmpeg and or mplayer
ffmpeg -i /path/to/whatever.wma
mplayer /path/to/whatever.wma

Try a wma in another player - gstreamer apps can play wma2, if on lucid the ppa in my sig will add wmas (voice) and wma3(pro) support

Edit 
a couple of views of mediainfo - 1st in 'easy' (wmal). 2nd in html (wma3pro

---

### Post by mc4man on 2010-09-17
> How would I find out if they're protected?
Any of the 3 methods mentioned will idenify the type of wma they are, and also should tell you if protected

Ex. ffmpeg
> doug@doug-laptop:~$ ffmpeg -i '/media/OS/Users/Doug/Desktop/audio/05 Fresh Air.wma' 
...clipped
[asf @ 0x895a470] DRM protected stream detected, decoding will likely fail!
....clipped
Stream #0.0: Audio: wmav2, 44100 Hz, 2 channels, s16, 349 kb/s

screen shows mediainfo on protected wma

To reinterate:
if the files are protected (encrypted) then you're out of luck
If the files are wmal (lossless) and you're on a 64 bit install then only a 32 bit mplayer will decode

---

