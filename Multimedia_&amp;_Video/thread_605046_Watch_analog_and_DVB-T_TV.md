---
title: "Watch analog and DVB-T TV"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by lospo on 2007-11-06
Hi, is there any software to watch Analog TV (standard antenna) and Dvb-T tv ? 
I can watch DVT trough Xine and analog tv trough TvTime. I'd like to watch tv with only one package (possibly usign a remote). I only see MythTV but it isn't what i need: it too much for me (a backend a frontedn.... naaaaaa i wan a very simple software...)

Thaks to all your replies!!!


Ciao

---

### Post by wieman01 on 2007-11-06
I would think that "Kaffeine" does just that. I use it for DVB-T but it should also support analog TV. It's in the repositories.
> sudo apt-get install kaffeine

---

### Post by Onurzaim on 2007-11-06
I am not able to watch analog TV in kaffeine. If there is someone I'd like him/her to lighten bath me.

---

### Post by Jose Catre-Vandis on 2007-11-06
Kaffiene doesn't play/watch analog tv.

You can use mplayer or vlc to watch both but you need to understand the configuration and command line syntax.

For mplayer I wrote myself a script a while back to handle TV watching. Have a look here it might give you some ideas

[http://ubuntuforums.org/showthread.php?t=369653](http://ubuntuforums.org/showthread.php?t=369653)

[http://ubuntuforums.org/showthread.php?t=338029](http://ubuntuforums.org/showthread.php?t=338029)

---

### Post by thorgal on 2007-11-07
I'm afraid MythTV is exactly what would do the job :)
You should not be so reluctant to try it out. It's easy to configure once all packages are installed. IIRC, you need :

mysql-server
mysql-client
some qt3-mysql stuff
mythtv-backend
mythftv-rontend
mythdatabase

then, depending on where you live, you either need xmltv or something else (if you live in the US, I cannot really tell) to fetch the program guide via internet.

I set up a debian based multimedia server, and it works great as a mythTV backend with a PVR500 card. My frontends are remote (e.g. laptops). All this works beautifully. It is really worth the effort. It took me about half a day to set this up but everyone in the house is very grateful for it. I also have another slave backend so that amounts to 3 tuners. No dispute as to what to watch at any moment ;)

---

### Post by thorgal on 2007-11-08
by the way, I forgot to mention, you don't even need the MythTV frontend. You can just use mythweb :) schedule recordings and watch them from any web browser (each recording will result in a web link to an .asx playlist on the mythweb page, so your server streams programs on demand by a simple click on the link). This is neat and I do use that a lot. If you want to stream beyond your LAN, there's a way for mythweb to trigger some transcoding on the fly so you can watch at a downgraded quality.

---

### Post by danmiddle2 on 2008-04-03
> **thorgal said:**
> by the way, I forgot to mention, you don't even need the MythTV frontend. You can just use mythweb :) schedule recordings and watch them from any web browser (each recording will result in a web link to an .asx playlist on the mythweb page, so your server streams programs on demand by a simple click on the link). This is neat and I do use that a lot. If you want to stream beyond your LAN, there's a way for mythweb to trigger some transcoding on the fly so you can watch at a downgraded quality.

How do I enable the on the fly re-transcoding in mythweb?

Thanks

Dan

---

