---
title: "How to install VLC 1.0.6 on Ubuntu/Lubuntu 10.10?"
date: 2010-10-24
forum: Multimedia Software
---

### Post by Cityscape on 2010-10-24
I have 3 computers running Ubuntu 10.10 (2x regular Ubuntu, 1x Lubuntu) and I need VLC media player 1.0.6 (the version from Lucid). I cannot use the Maverick VLC player, I need an older one.

What is the best way to install it? Is there a better option then installing it from source code?

---

### Post by mc4man on 2010-10-24
> Is there a better option then installing it from source code?
No, while if you assembled all the needed packages and installed the lucid packages for vlc, there could/would be numerous issues.
It may seem work ok depending on usage, but I believe things would start cropping up.
For one vlc wouldn't  close properly - it would actually just crash.
Other issues would arise because the lucid repo (or any lucid ppa) vlc would have been built off and depend on the 0.5.1 ffmpeg libs, maverick uses the 0.6 shared ffmpeg libs. 
Highly not recommended though you could try if desired
Probable package list (in this case amd_64
> doug@doug-laptop:~/Desktop/vlc6$ ls
libavutil49_0.5.1-1ubuntu1_amd64.deb
libebml0_0.7.7-3.1_amd64.deb
libmatroska0_0.8.1-1.1_amd64.deb
libmpcdec3_1.2.2-2.1ubuntu1_amd64.deb
libvlc2_1.0.6-1ubuntu1.2_amd64.deb
libvlccore2_1.0.6-1ubuntu1.2_amd64.deb
libx264-85_0.85.1448+git1a6d32-4_amd64.deb
vlc_1.0.6-1ubuntu1.2_amd64.deb
vlc-data_1.0.6-1ubuntu1.2_all.deb
vlc-nox_1.0.6-1ubuntu1.2_amd64.deb
vlc-plugin-pulse_1.0.6-1ubuntu1.2_amd64.deb

On my desktop mav I do have a vlc 1.0.6 package set I used for a bit back in May so you could certainly build the source and it should work ok. (it was statically linked to a ffmpeg and x264 builds just for vlc

I'd try to resolve your issues with 1.1.4 or even try the 1.2+ vlc instead

---

### Post by wojox on 2010-10-24
Just out of curiosity why can't you use Maverick VLC player?

---

### Post by Cityscape on 2010-10-24
> **wojox said:**
> Just out of curiosity why can't you use Maverick VLC player?
One of the main reasons I use VLC is for the shoutcast online radio feature. VlC 1.0.6 was the last version to include this feature, 1.1.x and onward don't have this feature. And I want this feature.

---

### Post by Cityscape on 2010-10-24
> **mc4man said:**
> 
On my desktop mav I do have a vlc 1.0.6 package set I used for a bit back in May so you could certainly build the source and it should work ok. (it was statically linked to a ffmpeg and x264 builds just for vlc

I'd try to resolve your issues with 1.1.4 or even try the 1.2+ vlc instead
So my best option is to install from source? I've never really installed from source, do you know of a good tutorial for installing VLC or other programs from source?

---

### Post by wojox on 2010-10-24
From what I understand 1.0 has reached end of life, but you can still install it here [At your OWN risks, install VLC from PPA]("http://www.videolan.org/vlc/download-ubuntu.html") , worth a shot.

---

### Post by andrew.46 on 2010-10-24
Hi Cityscape,

> **Cityscape said:**
> One of the main reasons I use VLC is for the shoutcast online radio feature. VlC 1.0.6 was the last version to include this feature, 1.1.x and onward don't have this feature. And I want this feature.

I don't know a great deal about Shoutcast except for the [vlc press release]("http://www.videolan.org/press/2010-1.html") but I see that vlc-git currently certainly *plays* Shoutcast streams themselves, I attach a screenshot of vlc-git playing this stream:

[http://yp.shoutcast.com/sbin/tunein-station.pls?id=1272871](http://yp.shoutcast.com/sbin/tunein-station.pls?id=1272871)

Or are you after a browseable list of streams as vlc currently does with icecast? Probably a better alternative to shoutcast imho...

Andrew

PS My apologies for inflicting goom on you as well :).

---

### Post by mc4man on 2010-10-24
> VlC 1.0.6 was the last version to include this feature, 1.1.x and onward don't have this feature. And I want this feature.
As Andrew has mentioned vlc can certainly play shoutcast streams, it just doesn't have the built-in listings anymore.
(you could create some and add to the media library 

A quick test w/ a built 1.0.6 using mav. libs suggests it will work [SIZE="1"]ok[/SIZE], certainly lacking in many things.
What will not work without patching (or ever) if how vlc closes.
I guess if one considers a crash as good as a close then no big deal.

without time and honestly inclination to willow out the build-deps, a good configure, some useful patches ect., this should build a working vlc 1.0.6

Before doing (if you do), I'd search vlc in synaptic and mark vlc-data for complete removal. All other vlc packages will then be marked for removal - go to each one and re-mark for complete removal.

Also go into home folder (view -> show hidden files) and remove the vlc folder in .config and .cache

Using maverick libs, minimal config, vlc-1.4 deps (some aren't needed, no big deal to have installed, assumes you don't have the 1.0.6 source
```
mkdir vlc6 && cd vlc6
```
```
sudo apt-get build-dep vlc && sudo apt-get install checkinstall
```
```
wget http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_1.0.6.orig.tar.gz
```
```
tar xzvf vlc_1.0.6.orig.tar.gz && cd vlc-1.0.6
```

Edited  [in from this thread]("http://ubuntuforums.org/showthread.php?t=1685734")
This would be a decent start

```
./configure --enable-libmpeg2 --enable-vorbis --enable-shout \
--enable-qt4 --enable-flac --enable-speex --enable-libmpeg2 --enable-theora \
--enable-twolame --enable-faad  --enable-v4l --enable-realrtsp --enable-real \
--enable-snapshot --disable-zvbi 

```
Followed by 
```
make
```

Or if some things error then add some disables like this 


```
./configure --with-tuning=native --enable-vorbis --enable-shout --enable-qt4 \
--enable-flac --enable-speex --enable-libmpeg2 --enable-theora --enable-twolame \
--enable-faad --disable-zvbi --disable-dv --disable-fluidsynth --disable-schroedinger \
--enable-v4l --enable-realrtsp --enable-real --enable-snapshot && make
```


```
sudo checkinstall --backup=no --deldoc=yes --deldesc=yes --delspec=yes \
--default --fstrans=no && sudo ldconfig
```

You can file this under poor idea, but then again I'm a firm believer in that one should do whatever they want (as far as this stuff

---

### Post by lapont on 2011-01-08
> **mc4man said:**
> 

without time and honestly inclination to willow out the build-deps, a good configure, some useful patches ect., this should build a working vlc 1.0.6

Before doing (if you do), I'd search vlc in synaptic and mark vlc-data for complete removal. All other vlc packages will then be marked for removal - go to each one and re-mark for complete removal.

Also go into home folder (view -> show hidden files) and remove the vlc folder in .config and .cache

Using maverick libs, minimal config, vlc-1.4 deps (some aren't needed, no big deal to have installed, assumes you don't have the 1.0.6 source
```
mkdir vlc6 && cd vlc6
``````
sudo apt-get build-dep vlc && sudo apt-get install checkinstall
``````
wget http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_1.0.6.orig.tar.gz
``````
tar xzvf vlc_1.0.6.orig.tar.gz && cd vlc-1.0.6
``````
./configure --with-tuning=native --enable-vorbis --enable-shout --enable-qt4 \
--enable-flac --enable-speex --enable-libmpeg2 --enable-theora --enable-twolame \
--enable-faad --disable-zvbi --disable-dv --disable-fluidsynth --disable-schroedinger \
--enable-v4l --enable-realrtsp --enable-real --enable-snapshot && make
``````
sudo checkinstall --backup=no --deldoc=yes --deldesc=yes --delspec=yes \
--default --fstrans=no && sudo ldconfig
```You can file this under poor idea, but then again I'm a firm believer in that one should do whatever they want (as far as this stuff
Thank you mc4man.
My concern is dvb-t and vlc 1.0.6 is the last version that plays the danish digital tv channels. I have tried your method in kubuntu maverick and it makes a working vlc 1.0.6. Just one thing does not work: Some of the danish channels are mpeg2 and some are mpeg4. The mpeg2 channels work but the mpeg4 channels do not play (no video, no audio).
Both mpeg2 and mpeg4 channels play flawlessly in kubuntu lucid with vlc from repository.
I have also tried your method i ubuntu natty alpha1 with same result as in maverick.

Is this some missing option to the configure

---

### Post by mc4man on 2011-01-08
> Is this some missing option to the configure 
As far as decoding mpeg4, I sorta doubt, fairly sure you could decode any of the various types from local files.

don't know much about dvb-t, you could just run a configure and then scrollback and read thru for what is and isn't enabled.
Maybe remove the --disable-dv though again don't know if related.

Otherwise start vlc from a terminal in verbose mode and see if anything of interest shows. Either -
vlc -vv
vlc -vvv

---

### Post by lapont on 2011-01-13
> Is this some missing option to the configure     No, I was wrong,  these options give a working vlc 1.0.6, but it is a bit too slow for DVB-T.
I have found this to be better:  
```
./configure --with-tuning=native --enable-vorbis --enable-shout \
--enable-qt4 --enable-flac --enable-speex --enable-libmpeg2 --enable-theora \
--enable-twolame --enable-faad  --enable-v4l --enable-realrtsp --enable-real \
--enable-snapshot
```I have now a working vlc 1.0.6 on kubuntu 10.10
Once again: Thank you mc4man.

---

### Post by jamestrowbridge on 2011-01-31
Thank you for this!  Hopefully Gmote is updated for the latest VLC player.. Ubuntu is prompting me to update.

---

### Post by kaneeec on 2011-09-06
Nothing worked for me until now. I found these packages and they work!
[https://launchpad.net/~ubuntu-security/+archive/ppa/+build/1926373]("https://launchpad.net/~ubuntu-security/+archive/ppa/+build/1926373")

---

