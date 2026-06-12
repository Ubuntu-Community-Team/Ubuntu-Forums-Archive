---
title: "MythTV Questions"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by galeron on 2007-08-25
Hi guys,

I'm moving into my new house in about 3 months time, and I'm intending to install MythTV for my living room.

I've got a few questions that I hope you guys can help me with. :popcorn:

1) I intend to split the frontend and the backend. If I want to watch and record TV, would the TV tuner be installed on the backend or the frontend?
2) Is there some kind of a plugin for karaoke? I'm not sure what this specifically entails, but what I have is a bunch of karaoke video files that I'd like to sing to ;) The problem now is that I want to be able to queue them. Is that possible?
3) For HDTV, what kind of hardware requirements are we talking about? My frontend is a Pentium 4 Northwood 2.4GHz with 512MB ram, Nvidia GeForce2 MX200. Essentially, old hardware.

Hope you guys can help! Thanks

---

### Post by Scorpuk on 2007-08-25
I can help you with your first question, but as for the other two I have no idea. Dont use karaoke files nor do I have HDTV reception :(


Anywho.


The TV tuner would be in the backend. 

If you are wanting to record TV and watch another TV station then you will need 2 tuners. Although it is nice to be able to record 2 stations at the same time too. :)

If you don't want to do this then you will be able to record TV and watch a previously recorded program at the same time.

---

### Post by PilotJLR on 2007-08-25
For the HDTV part, you'd need a better video card. You need something with a DUAL-LINK DVI output. Some cards output to component HD, which is okay too. From Dual-Link DVI, you can get either a dual link DVI-DVI cable, or a dual-link DVI to HDMI cable. This all depends on what input sources your TV will take.

Then of course, an HDTV tuner. The CPU will get slammed when Myth does commercial flagging, but if you dont' mind waiting then its okay...

I have a Core 2 Duo 1.86 in my mythbox, and running a commercial flag on an HD show takes about as long as the show itself.

---

### Post by galeron on 2007-08-25
Thanks, guys.

So to watch TV I just need to install the TV card on the backend and my frontend will retrieve the stream from the backend?

With regards to HDTV, do I need to change my processor as well, or would the graphics card alone suffice? I intend to skip the commercial flagging, of course.

---

### Post by Scorpuk on 2007-08-25
Yup the frontend will stream live TV, recorded TV, vidoes, music etc from the backend server.



As to your 2nd question you may find this some help - [http://mythextra.napsi.net/](http://mythextra.napsi.net/) - although not looked into all that much yet.


Kind of at work and not supposed to be surfing. Hey ho its the weekend. :)

---

### Post by galeron on 2007-08-25
Poor guy, who works weekends? Your boss is absolutely criminal, I say :P

Anyway, with regards to the karaoke thing, all I'm looking for is a "playlist" kind of thing so that I can queue up my videos. Would that be possible?

---

### Post by Scorpuk on 2007-08-25
So your "karaoke" videos are like music videos with the lil bouncing ball kind of thing over the words?


Lemme have a think :D

---

### Post by Scorpuk on 2007-08-25
A possible way round:


Import the karaoke video file into your mythtv database.


A guide can be found here: [http://www.myhdbox.com/mythtips/2006/05/tip-3-importing-downloaded-tv-shows.php](http://www.myhdbox.com/mythtips/2006/05/tip-3-importing-downloaded-tv-shows.php)

If you have a problem finding the script try this: [http://ubuntuforums.org/showthread.php?t=515225](http://ubuntuforums.org/showthread.php?t=515225)


When it asks you for the information I would suggest using "Karaoke" for the show name as the recordings list is sorted by this so you can select a show name to show all listings of that show (song) and then the name of the karaoke song as the subtitle. Since you need to enter a channel number try 01 as the channel number is not relevant.

ie.

Show name: Karaoke
Channel ID: 01
Subtitle: Take That - Hold On

etc.




Probably ;-)

Not tried running the script, but sometime after next weekend when I install my new backend server I will have to move my current recordings to it. 96 programs, using 206 GB (6 days 18 hrs 37 mins) out of 286 GB (43 GB free) and counting. :o



EDIT:

Hmmmmm not exactly a playlist though.... Although you could just manually move onto the next track...
Without being infront of my MythTV I'm not sure of all its options and not home until next weekend. :(

---

