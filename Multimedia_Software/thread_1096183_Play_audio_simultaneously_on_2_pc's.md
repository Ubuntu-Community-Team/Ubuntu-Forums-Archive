---
title: "Play audio simultaneously on 2 pc's"
date: 2009-03-14
forum: Multimedia Software
---

### Post by GuruMadMat on 2009-03-14
Hi everybody,

I would like to play audio simultaneously on 2 pc's.

Situation:

Server pc:
Ubuntu 8.04 server
MPD and lot's of MP3 files
location: living room

Client pc:
Ubuntu ??? server with low weight window management
(I still have to prepare this pc.

These pc's are connected with cat6 cable and gigabit nic
so it's fast enough. ( there are plans to stream tv recordings too)

I found this: [Network audio system]("http://www.radscan.com/nas.html")
I don't know if this is the solution to my problem.


Does anyone have any suggestion?

---

### Post by markbuntu on 2009-03-14
You can just turn on the pulseaudio rtp server


[http://ubuntuforums.org/showpost.php?p=6869726&postcount=5](http://ubuntuforums.org/showpost.php?p=6869726&postcount=5)

---

### Post by GuruMadMat on 2009-03-16
Will this play sound on the host and client simultaneously?

---

### Post by markbuntu on 2009-03-16
Yes, there will be some latency depending on your network but it will do that. On the host machine just make sure you select the rtp sink in the output device section of the pulseaudio volume control.

---

### Post by GuruMadMat on 2009-03-16
> **markbuntu said:**
> Yes, there will be some latency depending on your network but it will do that. On the host machine just make sure you select the rtp sink in the output device section of the pulseaudio volume control.

thank you for your reply :)

---

