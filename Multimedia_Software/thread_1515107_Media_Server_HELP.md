---
title: "Media Server HELP"
date: 2010-06-21
forum: Multimedia Software
---

### Post by hoffmaster on 2010-06-21
Ok I give up....

I am new to linux.  I guess maybe I don't know what I am looking for so I would really appreciate some guidance.

I have 3 PCs running windows (1 XP, 1 Windows 7 and 1 Vista) they all have windows media player 11.  I have a pretty good movie collection on my XP machine but I have resurrected a PC and stuffed it with hard drives.

All I want is to be able to use Windows Media Player to watch my videos from my Ubuntu machine.  As far as I can read I need a UPNP media server.  I have tried XBMC, VUZE and one other.  I open my Windows Media player on my Windows 7 machine and I can see the computer listed in the "Other Libraries" but no matter what I do I cannot find any videos in the library (same problem on the vista machine).  On my XP machine I cant even see the ubuntu machine.  

In XBMC I went and added a video to the library (BTW I hate XBMC because it wont just run silently in the background and is way bigger then I want).

Vuze seemed like it was the best thing ever made.  Unfortunately I cant figure out how to add videos that I didnt download to the Vuze library, and again I can see Vuze from the Vista and Windows 7 machines but cant find any videos in the library.

I almost tried MediaTomb or whatever, I had it installed but just got frustrated with my repeat failures.

I need to get this working with Media Player first because that is what my wife uses.  If it actually works I can migrate to a different player.  I am trying to slowly migrate away from Windows to linux because I cant afford to pay for it anymore and I am to responsible to pirate it anymore lol.

I am at my wits end lol.  Any help is hugely appreciated.

---

### Post by amauk on 2010-06-21
I'd use Samba

This way you can share folders over Windows' network neighbourhood, and you can just connect to the shared folders using any Windows (or indeed, any Linux) desktop machine

---

### Post by hoffmaster on 2010-06-21
So what is the purpose of a upnp media share?  

It seems I may have been so fixed on making the upnp media servers work that I overlooked the easy solution.  

I can just move the files to linux, share the folder and then add that folder to the windows media library path.

What again whats a upnp/DLNA server for?

---

### Post by amauk on 2010-06-21
I think uPnP is designed for non-configurable devices (network-aware AV receivers, and things)
but I've never used it, so don't really know

looking at the wikipedia page for uPnP, it looks far too complicated for it's own good....

---

### Post by amauk on 2010-06-21
double post

---

### Post by hoffmaster on 2010-06-22
I forgot to mention that I have an Archos TV+ that I use to stream to my TV.  It uses Upnp which is why I thought of it in the first place.  So I do need to get something working.

I tried ushare today and got that to actually work and show movies through media player but media player would not play until it had buffered the movie 100%.

I figured that this was the sort of thing people do in linux all the time.  But all I can find are specific distros like mythbuntu etc that are meant to be operated stand alone.  I want something to run silently making all my media available across my network.

---

