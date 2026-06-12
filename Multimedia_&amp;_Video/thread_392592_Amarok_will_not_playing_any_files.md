---
title: "Amarok will not playing any files"
date: 2007-03-24
forum: Multimedia &amp; Video
---

### Post by lsutiger on 2007-03-24
I have the KDE desktop installed. I am trying to play files in Amarok, but it ill not play any file I throw at it (mp3, wav)...It just sits there, some lines go through the analyzer ( the thing on the right of the volume bar)...Any suggestions?

---

### Post by kenmiles on 2007-03-25
I had this trouble when I first used Amarok and cured it by selecting a different audio driver in Settings menu.
Regards, Kenneth.

---

### Post by Daveth on 2007-03-25
open Amarok, then go to configure amarok, then configure engine, and then engine of the left hand side. Try setting the engine to Xine, and see what that does. Works fine for me.

---

### Post by lsutiger on 2007-03-25
Ken, thanx for the response! I do not see where I can change the drivers in KDE. Can you give me a 101?

Daveth...it is already set to xine?? Guess that not the problem, but thanx for the response!
BTW is Amarok the only iPod friendly music player for Ubuntu?

---

### Post by phr0z3n on 2007-03-25
> **lsutiger said:**
> Ken, thanx for the response! I do not see where I can change the drivers in KDE. Can you give me a 101?

Daveth...it is already set to xine?? Guess that not the problem, but thanx for the response!
BTW is Amarok the only iPod friendly music player for Ubuntu?

Nope, Banshee is ipod friendly. Integrates well with the gnome desktop though, and not KDE.:(

---

### Post by kenmiles on 2007-03-25
Settings - Configure Amarak - Engine -Output plugin

---

### Post by peterbengtsson on 2007-03-26
You might need to install xine first:

$ sudo apt-get update; sudo apt-get install gxine

---

### Post by lsutiger on 2007-03-28
>  kenmiles  kenmiles is offline
5 Cups of Ubuntu
	  	
Join Date: Jan 2007
Bean Count Hidden
Re: Amarok will not playing any files
Settings - Configure Amarak - Engine -Output plugin

It is set to Auto Detect

---

### Post by lsutiger on 2007-03-28
>  peterbengtsson  peterbengtsson is offline
First Cup of Ubuntu
	  	
Join Date: Mar 2007
Beans: 6
Re: Amarok will not playing any files
You might need to install xine first:

$ sudo apt-get update; sudo apt-get install gxine
__________________
work home hobby
Get reminded of old friends 

That did install a previously deselected library, but didn't work.

---

### Post by jfca283 on 2007-03-29
did you install this package 
**libxine-extracodecs**?
after installing it you can select the engine, use xine
and that's all
now you can play mp3

---

### Post by lsutiger on 2007-03-30
Just a question. I can play mp3's with other programs, I just want to use a program that is iPod friendly, but the problem seems to be just with Amarok. Also, the way that iTunes stores your music, by Artists/album/song and then an xml file to group them correctly into the cd's you rip ( as in if you had multiple artists on one cd)...is there a way to import this format into Amarok to make it make sense?
IE - on your hard drive it may be SomeArtist/Transistions/One song of a bunch on that cd, but in iTunes it shows all the songs under the same album.
Hope that doesn't make it more confusing :D
chown -r us ./base 
:D

---

### Post by lsutiger on 2007-03-30
Thanx jfca283, that worked!

---

