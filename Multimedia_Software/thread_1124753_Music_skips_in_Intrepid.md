---
title: "Music skips in Intrepid"
date: 2009-04-13
forum: Multimedia Software
---

### Post by alejobar on 2009-04-13
Hi guys, I have a little problem with ubuntu Intrepid, when I play music (mp3 format) through Rythmbox, sometime the sound just skips, I've been looking the system monitor and every time a song skip its because the processor goes all the way up to 100%, I'm not using anything else, just playing music so why is this happening?. I have all the recent updates, I tried turning of compiz and still the same problem. The computer have 512 of RAM and the processor its a AMD Athlon XP 2400 2.0ghz and i never had this problem before with Ubuntu Hardy. Here are the specs of my ubuntu pc:
[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00021854]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00021854")

Could someone please help me troubleshoot this?

---

### Post by djbushido on 2009-04-13
Have you tried using a different music player?
Also, check to see what audio driver Rhythmbox is using. Problems can occur if it is using OSS and you don't have that driver. Or Jack and don't have the server running.
But first, try using Amarok, and making sure to see if it is not something wrong with the file.
Also, are you playing an mp3 network stream, or a file?

---

### Post by alejobar on 2009-04-14
> **djbushido said:**
> Have you tried using a different music player?
Also, check to see what audio driver Rhythmbox is using. Problems can occur if it is using OSS and you don't have that driver. Or Jack and don't have the server running.
But first, try using Amarok, and making sure to see if it is not something wrong with the file.
Also, are you playing an mp3 network stream, or a file?

Hi DJbushido, I try Audacious because I know its lighter than Rythmbox, and I still have the same problem. This problem occurs very randomly, it could be at the beginning of a song, middle or end, and if I restart the song there's no problem, so I know for sure that the file its ok.

---

