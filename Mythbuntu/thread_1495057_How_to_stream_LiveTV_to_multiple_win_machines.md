---
title: "How to stream LiveTV to multiple win machines?"
date: 2010-05-27
forum: Mythbuntu
---

### Post by HereSomeHow on 2010-05-27
Hi, I already have a workig mythbuntu backend/frontend machine working, with a cheap analog TV card that records ok. What I need to do is to stream the livetv at "the same time" it is recording so multiple (3 or 4) computers can watch that feed. I'm bad at english, so I don't know if "stream" is the term I need, but what I need is that anybody that connects to the feed, picks it at the most "forward" point of the recording, not from the first second of it.

Rewinding would be nice for the clients, but I need them to pick the "live" feed and if there is no pause or slow motion or anything else, it's not important.

What should I try? I've already read a big bunch of VLC related pages, but still don't find if it is the way to go.

Any help is appreciated.

---

### Post by LowSky on 2010-05-28
I'm not positive this will work but here's my idea:

Install the MythTv fronted on the other machines. Using the computer with the primary backend, schedule your program to be recorded.

On the other machines use the MythTV frontend to watch TV. It should start on the recording channel during the live broadcast, and should allow rewinding if necessary.

The only issue I can foresee is if they try to change channels, I have no idea what might happen.

---

### Post by HereSomeHow on 2010-05-28
I need another way, 'cause all the clients are running windows XP, and the MythTV binary for windows that I found is a no go...

but thx anyway...

---

### Post by LowSky on 2010-05-28
The only other thing I can think of is Slingbox

---

### Post by sfp on 2010-05-28
MythTv Player

[http://www.sudu.dk/mythtvplayer/](http://www.sudu.dk/mythtvplayer/)

---

### Post by HereSomeHow on 2010-05-28
Sheez, the answer to mi needs is to stream with VLC, already tested it manually, with the gui of vlc in the backend.

What I wanted was to start recording a program, and a few seconds later start streaming it (making it available) to "anybody" in our lan, but as someone connected, that someone started at the "live feed" (obviously with those few seconds later).

I tested it, and streamed withot transcoding, directly from the .nuv file with the http option. Launched 3 different PC's with vlc as client and all 3 were showing it almost in sync, putting little CPU load.

Now, I've to figure out how to do it automatically, so 20 seconds after the start of the recording, vlc launches and starts streaming the World Cup matches!

Thx for your time, now anybody could point me on how to script that?

---

