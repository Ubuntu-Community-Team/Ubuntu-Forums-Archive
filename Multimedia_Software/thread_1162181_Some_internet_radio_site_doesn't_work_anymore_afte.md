---
title: "Some internet radio site doesn't work anymore after upgrade to Ubuntu 9.04 jaunty :("
date: 2009-05-17
forum: Multimedia Software
---

### Post by pieter333 on 2009-05-17
Hi,

I think since my upgrade to Ubuntu 9.04 jaunty some internet radio streams can't be played anymore.

For example: [http://www.radiofm.nl/stations/radio538hitzone.htm](http://www.radiofm.nl/stations/radio538hitzone.htm)

It worked always great, but can't get it to work anymore :( In Windows it works perfect.

I have al the gstreamer stuff installed and the ugly sets and ubuntu restricted area's. I also tried mplayer-mozilla instead of totem-mozilla, but it still doesn't work :(

Does anybody have an idea on how to fix this?

Thanks alot in advance!

Greetings,
Pieter

---

### Post by andrewc6l on 2009-05-17
Just a guess: do you have the non-free codecs installed in 9.04? It looks as if that is a Windows media player site.

I just tried on my 9.04 install, and I can play it direct from the command line with:
```
mplayer "mms://talpa06.streaming.is.nl/11103-WEB11_HQ"
```
so it may be a plugin issue with firefox.

---

### Post by albinootje on 2009-05-17
> **pieter333 said:**
> 
For example: [http://www.radiofm.nl/stations/radio538hitzone.htm](http://www.radiofm.nl/stations/radio538hitzone.htm)

It worked always great, but can't get it to work anymore :( In Windows it works perfect.


I'm using Ubuntu Hardy, and from that page you mentioned, [http://www.radiofm.nl](http://www.radiofm.nl), none of the 538 ones work and none of the Radio10gold work here with my setup.
A few others that I just tried which do work without problem for me are :
- Arrow Classic Rock
- Arrow Jazz
- Candlelight
- Radio 6
- Radio 5
- Radio 4
I've just tested this with Galeon and gecko-mediaplayer.

---

### Post by albinootje on 2009-05-17
> **andrewc6l said:**
> 
```
mplayer "mms://talpa06.streaming.is.nl/11103-WEB11_HQ"
```

That works fine for me here. But not within a browser with a mplayer based player.

---

### Post by pieter333 on 2009-05-18
Yeah, I have the same: mplayer "mms://talpa06.streaming.is.nl/11103-WEB11_HQ" works...


The non free codecs which package is that? When I search for "non free codecs" in Synpatic I don't find anything...

Pieter

---

### Post by pieter333 on 2009-05-18
I installed the non free codes with help of: [http://anotherubuntu.blogspot.com/2009/03/non-free-codecs-for-jaunty.html](http://anotherubuntu.blogspot.com/2009/03/non-free-codecs-for-jaunty.html)

But that didn't solve the problem.... :(

---

### Post by albinootje on 2009-05-18
> **pieter333 said:**
> I installed the non free codes with help of: [http://anotherubuntu.blogspot.com/2009/03/non-free-codecs-for-jaunty.html](http://anotherubuntu.blogspot.com/2009/03/non-free-codecs-for-jaunty.html)

But that didn't solve the problem.... :(

The problem must be with the browser-player and/or the browser that we're using.

Perhaps this one will work fine with it in Wine :
[http://sourceforge.net/projects/guliverkli/](http://sourceforge.net/projects/guliverkli/)

---

### Post by pieter333 on 2009-05-26
Does anyone know where I can report this bug?

---

### Post by albinootje on 2009-05-26
> **pieter333 said:**
> Does anyone know where I can report this bug?

[http://bugs.launchpad.net/](http://bugs.launchpad.net/)

---

### Post by pieter333 on 2009-05-26
Ok, thanks!

---

