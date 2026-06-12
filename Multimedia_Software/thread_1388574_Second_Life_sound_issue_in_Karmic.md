---
title: "Second Life sound issue in Karmic"
date: 2010-01-23
forum: Multimedia Software
---

### Post by marcozs on 2010-01-23
After Karmic upgrade, I was experiencing issues with sound and SLvoice with Second Life and for that reason also a very high cpu load.
After looking on the net a lot I found a solution which I thought to share: it's enough to put into ${SECONDLIFE_INSTALL_DIR}/lib the content of this pack:
[http://dl.dropbox.com/u/1111567/Archivio_Sito_Web/SLCompatLib.tar.gz](http://dl.dropbox.com/u/1111567/Archivio_Sito_Web/SLCompatLib.tar.gz)

After that no more sound issues and no more high cpu load!
Tried it on Snowglobe from getdeb ( [http://www.playdeb.net/updates/ubuntu/9.10/?q=snowglobe](http://www.playdeb.net/updates/ubuntu/9.10/?q=snowglobe) ) but it should work fine also on the official player and on Openmetaverse one.

Check out the source if you want (in Italian):
[http://gersar.netsons.org/?p=70](http://gersar.netsons.org/?p=70)

ciao!

---

### Post by Jheric on 2010-02-14
Hmm... that just killed my sound altogether.

Sigh...

---

### Post by TyTiger on 2010-02-20
thanks dude this really fixed it for me, Since pulse is woven deeper than it used to be in the 8.X versions of ubuntu just removing pulse is allot of hassle now on 9.x but this was really simple and seemingly fixed the issue.

I totally recommend giving it a go before taking more drastic and headachey' options.

---

### Post by locote on 2010-03-08
see i could hear the sounds and the voice chat, but I could never hear the music.  Anytime I go somewhere i don't hear the music.

---

### Post by locote on 2010-03-22
if this dont work for you, like it didn't work for me check this one out"

[http://ubuntuforums.org/showthread.php?t=1322639](http://ubuntuforums.org/showthread.php?t=1322639)

---

### Post by c0rrupt0r on 2010-04-23
I been messing with my sound in Ubuntu 9.10 and Secondlife for a few weeks now and nothing seemed to work,
I finely found a simple little problem that seemed to have worked for me and hopefully works for someone else,

I went to my volume control Icon on my Panel and right clicked then to the output tab to my balance Adjuster, and moved it a bit to the right and that fixed my crackling and popping and messed up sound all together,
I have found there is something wrong while its placed in the middle. good luck all and hope this helps some others.

---

