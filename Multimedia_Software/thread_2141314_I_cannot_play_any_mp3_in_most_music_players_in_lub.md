---
title: "I cannot play any mp3 in most music players in lubuntu 13.04"
date: 2013-05-02
forum: Multimedia Software
---

### Post by SangeetKhatri on 2013-05-02
I cannot play mp3 in most music players mainly banshee which is my favorite, going in the ubuntu IRC Channel they told me to install lubuntu-restricted-extras but even after installing that it is not working, please could anyone tell me what to do

Also running banshee in debug mode from the terminal i am getting the output in the link below, maybe this helps..
[http://paste.ubuntu.com/5625882/](http://paste.ubuntu.com/5625882/)

Also i can run mp3 in audacious and VLC but not in banshee, Rhythmbox and xnoise and also lxmusic . These are the ones i tested.

---

### Post by Yellow Pasque on 2013-05-03
Are you using JACK server? That's what it looks like banshee (or more specifically, gstreamer) is trying to output to.
Note that rbox, banshee, and xnoise all use gstreamer...

---

### Post by SangeetKhatri on 2013-05-03
What is a Jack Server?? I am sure that i am not running any server, btw even after installing the update of Rhythmbox i am unable to play any file
And i cannot even play videos in Banshee, this is not at all going good so far and ubuntu should release a fix for this in about 2-3 days!!

---

### Post by Yellow Pasque on 2013-05-03
If you don't know what jack is, then you're probably not using it.
Let's see if we can play a sample sound using gstreamer:
```
sudo apt-get install gstreamer1.0-tools dconf-tools
gst-launch-1.0 audiotestsrc ! audioconvert ! audioresample ! autoaudiosink
```
Any sound? If not, let's try alsasink explicitly:
```
gst-launch-1.0 audiotestsrc ! audioconvert ! audioresample ! alsasink
```

---

### Post by SangeetKhatri on 2013-05-03
I tried both the commands you gave me, this is the output i get 

1st Command paste : [http://paste.ubuntu.com/563005/]("http://paste.ubuntu.com/5630005/")
2nd Command paste : [http://paste.ubuntu.com/5630007/](http://paste.ubuntu.com/5630007/)

and i still cannot hear any mp3 in banshee, well please take a look at the 2nd paste as it says something not found, maybe that is why the problem is there..

Anyways thanks for support, and reply as soon as you can :)

---

### Post by Yellow Pasque on 2013-05-03
I'll get right on it :) :) :) ;)

---

### Post by Yellow Pasque on 2013-05-03
```
sudo apt-get install gstreamer1.0-alsa
```
;)

---

### Post by mc4man on 2013-05-03
Try removing the .bin file in  
~/.cache/gstreamer-1.0/

---

### Post by SangeetKhatri on 2013-05-04
I removed the .bin file in that folder and also did installed and guess what, Now i am able to play any mp3 i throw at banshee..
Thanks a lot guys, loved the fast support you gave me, now i can enjoy Enrique Iglesias tracks that i love so much!!

ThankYou All for helping me!!

---

