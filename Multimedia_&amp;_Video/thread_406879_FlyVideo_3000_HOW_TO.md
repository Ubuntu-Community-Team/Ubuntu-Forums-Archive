---
title: "FlyVideo 3000 HOW TO???"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by abena on 2007-04-11
[I][COLOR="DarkRed"][FONT="Comic Sans MS"]	
Exclamation About tunning up the FlyVideo 3000
Hi, I all ready have the tvtunner card recognized, but everytime I open some aplication to watch tv, it just falls down, I have no way to try the working of the card, I've tryng with several aplications: XawTV, TvTime (wich is the only one the doen't falls down, but I says "No input signal"), MPlayer... etc.

Any idea?[/FONT][/COLOR][/I]:KS

---

### Post by cpicon92 on 2007-04-25
see [http://ubuntuforums.org/showthread.php?t=76637&highlight=flyvideo+3000](http://ubuntuforums.org/showthread.php?t=76637&highlight=flyvideo+3000)

---

### Post by abena on 2007-04-26
*[COLOR="DarkRed"]Thanks, for the link, but unfortunatly, it didn't work... so, I have a new dude, can some one please post its module file, 'cause all ready I don't what should I have in ther[/COLOR]*e!

---

### Post by medeshago on 2007-04-29
> **abena said:**
> *[COLOR="DarkRed"]Thanks, for the link, but unfortunatly, it didn't work... so, I have a new dude, can some one please post its module file, 'cause all ready I don't what should I have in ther[/COLOR]*e!

This is what i did:

sudo gedit /etc/modprobe.d/saa7134

and added:
#flyvideo
options saa7134 card=3 tuner=39 gbuffers=4

sudo gedit /etc/modules

and added:
saa7134 card=3 gbuffers=4

My card is a Flyvideo 2000. It works great with tvtime, haven't tried with anything else.

---

