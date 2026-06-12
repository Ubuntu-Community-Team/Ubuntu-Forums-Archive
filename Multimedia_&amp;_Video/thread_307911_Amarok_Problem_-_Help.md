---
title: "Amarok Problem - Help"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by pejpm on 2006-11-27
Hi, i recently just made the switch from winxp to ubuntu. I wanted something to manage my ipod and mp3's to i installed amarok. I have two issues with it that are driving me crazy, i'd love it if someone could help.

1. Whenever i try to play m4a files (which make up 90% of my collection), it says that no decoder is available. Anyone know how i add m4a support? It recognises the files and adds them to my library, its just doesnt play them.

2. I just copied my 2000 files into my home folder and amarok is scanning thorugh them adding them to the library. It gets to 55% completed, and stays on 55% for about 5mins, and then my computer totally freezes and i have to switch if off. Any ideas what this could be? I presume a rogue file is stopping it working, anyone know if there is any way of viewing what file it gets to adding to the library before crashing?

3. If anyone has any suggestions on what I can use besides amarok (i dont know if amarok is that good, whats the general consensus?)

---

### Post by Sarisar on 2006-11-27
> **pejpm said:**
> Hi, i recently just made the switch from winxp to ubuntu. I wanted something to manage my ipod and mp3's to i installed amarok. I have two issues with it that are driving me crazy, i'd love it if someone could help.

Well I'll try - had some problems myself with Amarok but all sorted now

> **pejpm said:**
> 1. Whenever i try to play m4a files (which make up 90% of my collection), it says that no decoder is available. Anyone know how i add m4a support? It recognises the files and adds them to my library, its just doesnt play them.

Don't use M4A myself, have lots of MP3s ripped from my own CDs.  So can't help here, sorry.

> **pejpm said:**
> 2. I just copied my 2000 files into my home folder and amarok is scanning thorugh them adding them to the library. It gets to 55% completed, and stays on 55% for about 5mins, and then my computer totally freezes and i have to switch if off. Any ideas what this could be? I presume a rogue file is stopping it working, anyone know if there is any way of viewing what file it gets to adding to the library before crashing?

Run it from a command prompt (terminal in Linux of course but thought I'd use the XP terminology).  Simply run Amarok.  When it scans your collection it should say each and every file it runs.  Simply run it until it crashes / hangs and check the terminal for the last file mentioned.  Move it somewhere else (so Amarok won't scan it) and try again.  I had a corrupted file when I tried (0 byte file I think it was)

> **pejpm said:**
> 3. If anyone has any suggestions on what I can use besides amarok (i dont know if amarok is that good, whats the general consensus?)

Amarok is what I use, but there are others (as always in Linux.  A friend uses gtkpod but he had various problems setting it up.

Hope that helps, and if someone else could explain M4a files :)

---

### Post by pejpm on 2006-11-27
ok, so total noob question...but how do i run amarok from the command line?

---

### Post by pejpm on 2006-11-27
oh, i managed to get m4a support working. i installed xine, and this has support for m4a which i guess amarok uses somehow....

i just ran amarok from comman line by simply typing amarok, but it doesnt tell me what files it is trying to add, it just says "kio (KIOConnection): ERROR: Header has invalid size (-1)"

---

### Post by Sarisar on 2006-11-28
> **pejpm said:**
> oh, i managed to get m4a support working. i installed xine, and this has support for m4a which i guess amarok uses somehow....

i just ran amarok from comman line by simply typing amarok, but it doesnt tell me what files it is trying to add, it just says "kio (KIOConnection): ERROR: Header has invalid size (-1)"

Sorry I should have said run 'amarok' meaning the command.

So I've looked around and don't know how to help get around that problem short of pulling some MP3s out to find which file it is (say pull A-M into another directory that isn't scanned and see if N-Z crashes it).

There must be a better solution but I don't know what it is - amarok must have updated because I'm sure I just ran it from the command line to see the files being scanned.  Or maybe I'm just going mad.

Sorry I can't be more help

---

### Post by pejpm on 2006-11-29
update!! ok, so i thought my machine was crashing when trying to scan my collection, but it seems not. I noticed that whilst nothing would respond (not even num lock!!) it was just really busy!! I left the machine stuck at 45% scanned, and after 15mins it finished!! It turns out there was a couple of rm files buried deep in my collection somewhere that were causing problems, but now all is good! Just need to get amarok to recognise my ipod now!!!

---

### Post by Sarisar on 2006-11-30
And I just found a way to search for zero byte MP3s!

I didn't have any problems with my iPod and Amarok, although I had installed a ton of stuff for it trying to get it to work with other programs like Rhythmbox.  I think the important one you need is 'ipodslave' for Amarok (let me know if it is will you).

---

### Post by pejpm on 2006-11-30
well, the strange thing is, i just installed edgylast week and hadnt bothered to install anything for my ipod yet as it wasnt really a priority, but last night i plugged my ipod in and rhythm box recognised it straight away! obviously I'd rather use amarok though so I'll try ipodslave tonight and let you know.

---

