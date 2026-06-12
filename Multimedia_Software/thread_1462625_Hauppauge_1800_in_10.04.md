---
title: "Hauppauge 1800 in 10.04"
date: 2010-04-25
forum: Multimedia Software
---

### Post by LeonhartBA on 2010-04-25
First of all, greetings everyone

I have been trying to get my Hauppauge 1800 to work with Ubuntu 10.04, but no luck. I get some picture and no sound.

I am just wondering if anyone was successfully in getting this card to work, and if so what have you done. I have tried a few things I found around the net, but no luck with that either. 

I am currently trying the ways descried here: 

[http://ubuntuforums.org/showpost.php?p=6129026&postcount=132](http://ubuntuforums.org/showpost.php?p=6129026&postcount=132)

It is for a very old version of Ubuntu, so I am hoping I dont do even more harm to the whole situation. If anyone has any ideas how to get this card working please let me know. Majority of things I have found are for old distros, many things changed since than.

Lack of TV is the only thing that is keeping me from fully switching to Linux. Solving this matter will finally put me at peace and I can say goodbye to Windows for good. 

Thank you for any help

---

### Post by WinterRain on 2010-04-26
Check this out: [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800)

---

### Post by LeonhartBA on 2010-04-26
Thank you for quick response.

I already used tvtime/mplayer. Tvtime gives me picture, but n audio. If I use mplayer as the link mentions, I lose picture quality but get audio.

I have a preference for mythtv due to the dvr functionality. I it odd that I can get crystal clear picture in tvtime, but bad quality in mythtv.

I will get back to tinkering some more tomorrow. I post any results I do get

If anyone else has any suggestions, do let me know. Thank you

---

### Post by jbartosh on 2010-04-30
I am running this same card under Mythbuntu 10.04.  I'd like to know what you've put in MythTV just to get through the basic setups.  I cannot not get as far as having a picture of any kind, because it will not even recognize a signal from the capture card.  It only recognizes the hauppage under anolog, giving the correct info, but does not recognize it at all in DVB-T digital.  If you could briefly describe how to get through setting up the backend to work with this card I would sure appreciate, and would let you know if I could get any type of picture going with it.  Thanks!

---

### Post by GWBouge on 2010-05-01
Not so sure about the 1800, but I managed to get my WinTV-1600 working pretty easily with VLC.

With a fresh Ubuntu 10.04 64-bit install:
```
sudo apt-get install vlc
sudo apt-get install ivtv-utils
ivtv-tune -c 3
vlc /dev/video0
```

that just installed VLC Media Player, some ivtv utilities (so I could tune the card), tuned the card to channel 3, then started up VLC with the video card as the only argument.  seems to be working quite well, didn't take any restarts or anything.  MUCH easier than what I had to go through in previous versions of Ubuntu, lol.

but, as far as dvr/recording ... dunno  =o(

---

### Post by jbartosh on 2010-05-01
I have been considering just going to VLC.  As I don't do a lot with TV, mostly just videos, very rarely record tv but nice to have that option.  If I do though, I'd like to get something to where I could at least change the volume with my Windows Media Center remote...  That's where the nice interface of MythTV would have been nice.

---

### Post by jbartosh on 2010-05-01
I'd like to update, if someone could help me out...

I can scan all of my channels with w_scan and they come up fine.  However, the channels.conf is very small (only a sentence long when opened with text editor) and I don't know how to get this channel info to MythTv or anything else for that matter?

The system recognizes my tuner card fine from everything I can see...

I can use ivtv-tune to tune to the frequencies that were listed from the w_scan (i.e. 503000mhz) and it says "signal detected" and something like playing in /dev/video0

I can't get mplayer or vlc to play /dev/video0, mplayer says it is a text file...

If I try cat /dev/video0 the test file (.mpg) does not play in anything.  Mplayer says it is a text file again...

Any ideas on why myth won't get the channels in or if I can manually enter the frequencies from w_scan into Myth?  Must be something I can do if the channels scan with their correct names and everything?  The card must be working, I just need some output...

---

### Post by jbartosh on 2010-05-01
Just wanted to add this in case anybody can use it.  My primary problem was not setting a starting channel in the backend settings.  There is an option to do that, the channels did scan into MythTV, just would'nt show up in "watch tv" until the intial channel was set.

---

