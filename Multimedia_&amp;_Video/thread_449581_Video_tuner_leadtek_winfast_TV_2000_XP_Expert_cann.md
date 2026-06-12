---
title: "Video tuner leadtek winfast TV 2000 XP Expert cannot configure"
date: 2007-05-20
forum: Multimedia &amp; Video
---

### Post by Eliadar on 2007-05-20
I read carefully all posts regarding tv tuners & Leadtek & winfast configuration
Tried tuner=5  or 43 (nevertheless tried 2,3,4,6,,38 )
Still when i "tvtime" i get a flash of black window... nothing more.
What shall i do next because i fell like stuck...
(copied & pasted all codes written in many posts and stuff, cleared and changed numbers stil i could not go further that 1 second black window)

Any info welcome, thanks...

Eliadar

---

### Post by streamx on 2007-05-24
I have exactly the same problem. Only black screen, no sound or video.

---

### Post by Eliadar on 2007-06-06
I solved the problem by removing the TV tuner :(
So thread closed.

---

### Post by streamx on 2007-06-06
Yes, but it's not a real solution... :( I don't want to buy a new one, my old one is working really good under Windows and I don't have spare money...

---

### Post by grege on 2007-06-08
The simplest way to watch TV under Linux is to use Kaffeine. If your card is recognised and you have a /dev/video0 then start Kaffeine and a DVB icon shouldl be available. In the menus find DVB then channels and set your area and do a channel scan.

TV time xatv mplayer vlc xine all require much mucking about with tzap to create a channels.conf before you can do anything.

Kaffeine also has facilities to record and playback, timers etc.

You will need win32codecs installed to decode the .ts stream

:)

---

### Post by OzzyFrank on 2007-08-29
Yep, I've tried it all, from BTTV, modprobe, changing numbers left right and centre in any config file pointed out... the system sees the card, but nothing like Kaffeine or dedicated TV programs can. Tvtime and MythTV just give me a black screen too. Tried accessing the FM via a few apps, nothing. Yet, some people do in fact run the TV Expert 2000 fine, radio and tv/video. Go figure. I too would love to be able to use this card, and not pull it out and buy a new one. Any takers??

---

### Post by beefbowel on 2007-11-11
how do you get this tv tuner card to work?  what do you do to install drivers?

---

