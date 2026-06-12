---
title: "amarok does not display cddb info"
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by brazzmonkey on 2007-11-16
hi everyone,

lately i noticed amarok doesn't show cd info from freedb, whereas other kde apps do.

using xine engine, config is the following :
default device : /dev/scd0
cddb server : freedb.freedb.org
port 8880

any hint ?

*edit*
ok, don't ask me why, SOMETIMES it works&#8230;
i'dd say generally speaking, amarok behaves oddly when it comes to play audio cd (takes a while to start, seems to slowly scan the cd, etc.).
other apps are straightforward, detect and play CD in a matter of seconds&#8230;

---

### Post by Saint Angeles on 2007-11-30
yeah i have to type it all in manually... what gives?


(bump)

---

### Post by gotgenes on 2007-12-06
freedb.org is dead.

Try switching the server over to musicbrainz.org:
[http://wiki.musicbrainz.org/FreeDBGateway](http://wiki.musicbrainz.org/FreeDBGateway)

---

### Post by brazzmonkey on 2007-12-06
[http://www.freedb.org/](http://www.freedb.org/)

looks like it's still there&#8230;

---

### Post by logos34 on 2007-12-06
no answer at freedb this morning...was working fine yesterday.

---

### Post by Keronn on 2007-12-07
It doesn't work for me too, with amarok and kaffeine (kafffeine also takes a very long time to open an audio cd). 
But it seems to work better with KsCD (using the same server), that's weird.

---

### Post by logos34 on 2007-12-07
> **Keronn said:**
> It doesn't work for me too, with amarok and kaffeine (kafffeine also takes a very long time to open an audio cd). 
But it seems to work better with KsCD (using the same server), that's weird.

try one of the mirrors listed in[ this thread]("http://ubuntuforums.org/showthread.php?t=632904").

freedb.berlios.de

and 

[URL="http://www.gnudb.org/howto.html"]gnudb.gnudb.org
[/URL]
are working fine today.

---

### Post by brazzmonkey on 2007-12-08
thanks for the tip, that's a useful resource !

---

### Post by Keronn on 2007-12-08
Yes, thanks ! It works very well with kaffeine and I use this application now. 
 
Concerning  amarok, it seems that it's not only a server's problem in my case. It doesn't recognize cd with any of these mirrors. I've tried with a new amarok's profile : it doesn't works more.

---

### Post by GnuSense on 2007-12-08
Amarok is just a particularly braindead application, how do I loathe it, let me count the ways?  

1. It is glacially slow and will happily bog your entire system when you just want to play a song in the background.

2. It is not particularly configurable compared to average KDE programs.

3. It is fragile, it spawns multiple processes and then confuses itself and won't stop without the command line, if then.  I've probably used the command 'killall amarokapp' more times than all other 'killall' commands together (and I don't like Amarok and prefer to use XMMS!)

That said, I still use it because that seems to be the way Linux music players are going, away from fast, small, "the Linux way" and towards huge, slow, buggy suites a la WMP or iTunes (which I also hate),.

Brazzmonkey, probably your problem is Amarok's choice of your default device : 
/dev/scd0

I don't think that is correct. My advice would be to do a 'ls /dev/cdro*' and use that value instead, in my case:
/dev/cdrom1

---

### Post by ganymede62 on 2007-12-08
GnuSense smells funny. He's a smelly guy. He make me laugh funny!

---

