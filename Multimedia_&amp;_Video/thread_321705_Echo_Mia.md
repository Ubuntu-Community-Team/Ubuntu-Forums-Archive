---
title: "Echo Mia"
date: 2006-12-19
forum: Multimedia &amp; Video
---

### Post by Xecuter on 2006-12-19
I need to find some drivers and such for my Echo Mia sound card. Does anyone know of a good guide or something to follow?

---

### Post by ssavelan on 2007-02-28
In fact, I do.  I adapted these directions for my echo layla:

[https://help.ubuntu.com/community/EchoMia]("https://help.ubuntu.com/community/EchoMia")

they still work well last time I used them.  Having just the Echo alone has been a bit more reliable than trying to run two soundcards.  I wouldn't use the preferences>>sound>>default drop menu.  I think that has screwed my sound a couple of times.  It is best to get down and dirty with the .conf files and such as indicated by the howto.  Don't get lazy; everything works well until you get lazy and try to make Ubuntu do solmething for you (like change your default soundcard.

The directions in the above link should take care of you.  I recommend the latest version of ALSA, rather than the stable, it gets better all:guitar:  the time.

---

### Post by ssavelan on 2007-02-28
I hope that you are are either subscribed to his thread or have already found the solution .  

I thought that it was interesting to see that you are from Norway.  I live in Georgia, USA but have Norwegian heritage/name.  How's Norway? (might try to escape USA)

I have Echo layla24.  Small world.

The Echo drivers in the latest test build of ALSA run great.  Definitely build them from source per the instructions above.  You will probably never run it on windows again; I haven't.

---

### Post by Xecuter on 2007-07-22
> **ssavelan said:**
> In fact, I do.  I adapted these directions for my echo layla:

[https://help.ubuntu.com/community/EchoMia]("https://help.ubuntu.com/community/EchoMia")

they still work well last time I used them.  Having just the Echo alone has been a bit more reliable than trying to run two soundcards.  I wouldn't use the preferences>>sound>>default drop menu.  I think that has screwed my sound a couple of times.  It is best to get down and dirty with the .conf files and such as indicated by the howto.  Don't get lazy; everything works well until you get lazy and try to make Ubuntu do solmething for you (like change your default soundcard.

The directions in the above link should take care of you.  I recommend the latest version of ALSA, rather than the stable, it gets better all:guitar:  the time.

Long time since i've been here. Hehe.

Well I finally got the drivers working. But I'm using two sound cards, i have to. 

Now I'm trying to get it to work with Ardour. But i can't get audio into Ardour.

Is there a program that monitors every input and output and shows that there is activity there? I need to know if the drivers are working.


I've plugged my guitar-amp into IN 1 on the Mia, how do i tell Ardour to listen to that channel?


Norway is great! :D The best :P

---

### Post by fredj on 2007-07-22
Ardour works through the Jack sound server so you need to get that up and running.

---

### Post by ssavelan on 2007-07-23
> **Xecuter said:**
> Long time since i've been here. Hehe.

Well I finally got the drivers working. But I'm using two sound cards, i have to. 

Now I'm trying to get it to work with Ardour. But i can't get audio into Ardour.

Is there a program that monitors every input and output and shows that there is activity there? I need to know if the drivers are working.


I've plugged my guitar-amp into IN 1 on the Mia, how do i tell Ardour to listen to that channel?


Norway is great! :D The best :P

Indeed, do you have Jack?  You need like qjackctrl and some other stuff.  You can get it all in a package manage.  Get Jack up and running before anything else.  Jack-setup will help you diagnose whether your drivers are up.

---

