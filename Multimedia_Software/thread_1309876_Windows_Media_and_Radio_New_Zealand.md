---
title: "Windows Media and Radio New Zealand"
date: 2009-11-01
forum: Multimedia Software
---

### Post by notrublw on 2009-11-01
Having junked Vista and installed 9.10 (Karmic Koala), I've found that most Windows Media Streams work, e.g. CBC Radio at 
               [http://www.cbc.ca/listen/index.html#](http://www.cbc.ca/listen/index.html#)
However Radio New Zealand's streams at
                [http://www.radionz.co.nz/](http://www.radionz.co.nz/)
e.g.
                [http://www.radionz.co.nz/audio/live/national/adaptive.asx](http://www.radionz.co.nz/audio/live/national/adaptive.asx)
are dead in the water.  Any suggestions?

This is somewhat amusing because Time-Warner/Roadrunner streams a service called Music Choice to its cable customers and as Roadrunner Radio to its
ISP customers.  Neither I nor the Roadrunner help desk could make Roadrunner Radio (Windows media based) work under Vista, whether I used Firefox or IE.  Under Ubuntu it works perfectly.

Why New Zealand?  Because its one of those places I used to hunt for through the static, interference and fading of shortwave radio.  Now I can get it on the internet.  Neat, no?

---

### Post by notrublw on 2009-11-15
I found some time to do some searching--and found 1 suggestion to open movie player and then to cut/paste the link into it.  That works, which suggests that the correct codec is installed.  I next looked into the mime type/application connection specified in firefox, and that looked ok.  So I kind of stumped--maybe it has something to do with the way the web page is coded.  At any rate I can listen to radio new zealand when I want to.

---

### Post by Rumpty on 2009-11-15
Hi notrublw. I also go to the RadioNZ website now and then, (I live in NZ) and find their streaming files are unpredictable, as to whether or not they will play (stream) in Ubuntu.

 At the moment the link you give streams fine, the plug-in obviously works. But the links to past programs on their site will not work for me right now, streaming or even if I cut/paste the link into Gnome-mplayer. They are all .asx files, so...?

---

### Post by andrew.46 on 2009-11-16
Hi notrublw,

> **notrublw said:**
> [http://www.radionz.co.nz/audio/live/national/adaptive.asx](http://www.radionz.co.nz/audio/live/national/adaptive.asx)


You can play this one from the commandline with MPlayer:
```

mplayer -playlist http://www.radionz.co.nz/audio/live/national/adaptive.asx
```

vlc also plays this if the commandline is not your taste :).

Andrew

---

### Post by Rumpty on 2009-11-17
Ashes of Time - Redux, of course?

---

### Post by andrew.46 on 2009-11-17
Hi Rumpty,

> **Rumpty said:**
> Ashes of Time - Redux, of course?

Of course :). 

Andrew

---

