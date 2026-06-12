---
title: "Here's what I want to do..."
date: 2009-09-16
forum: Mythbuntu
---

### Post by rdhaines1966 on 2009-09-16
I'm brand new to Mythbuntu.  I've downloaded it.  That is as far as I've gotten.  I have installed Ubuntu on several occassions and I'm not completely new to Linux although, I wouldn't consider myself an expert by any means.
 
So here's what I want to do.  I want to build a media center that will I can do the following things.
 
Rip my DVD movies to disk to be pulled up and watched via a menu.  Perhaps by genre.
 
Listen to my MP3 collection and build play lists for music.
Watch home videos and pictures.
 
Recording and watching live TV is secondary to me, although it would be nice.  I'm told this is next to impossible if you have DirectTV, which I do.
 
Mostly I just want first few things that I mentioned all built around an intuitive menu driven interface.  I want to build a theater room in my home and use this for watching movies and and pipe music of my choosing throughout my house.
 
Can someone please answer the following questions?
 
1.  Will Mythbuntu do these things?
2.  How difficult will this be to setup?  I work in IT and have access to a couple of people who I WOULD consider Linux experts.
3.  Please explain the server and client configuration.  I would like to do this with a minimal amount of hardware.  Will I need a client and server?  If I go this route can the client operate over a wireless network and perform well?
4.  I want to build this thing right, so is there a hardware compatibility list that I can follow to get the best of the best hardware?
 
Thanks to anyone willing to help me get these questions answered.  I'm anxious to get started.

---

### Post by oldsoundguy on 2009-09-16
start here:

[http://www.mythbuntu.org/installation_manual](http://www.mythbuntu.org/installation_manual)

then put mythbuntu into Google and have at it.  Especially the Mythbuntu Forum!
Just like this Ubuntu forum, you will find some really knowledgeable peeps there that understand that not everyone is born knowing everything about computers and they will, as does this forum, answer your questions.  Just be sure to get the question into the title of your thread as that will garner not only MORE responses, but quicker responses.

---

### Post by SiHa on 2009-09-16
Although MythTV is great, it is essentially a PVR with the other media centre bits bolted on. The UI for Mythvideo and Mythmusic isn't the best - although with the upcoming release of 0.22 they do look better.
Perhaps if TV is secondary, you might be better looking at XBMC / Boxee?

---

### Post by williammanda on 2009-09-17
> **rdhaines1966 said:**
>  
Rip my DVD movies to disk to be pulled up and watched via a menu.  Perhaps by genre.

Genre is not implimented. But it will rip dvd's
 
> Listen to my MP3 collection and build play lists for music.
Watch home videos and pictures.

Yes you will be able to watch videos and review pictures, not sure about mp3s.
 
> Recording and watching live TV is secondary to me, although it would be nice.  I'm told this is next to impossible if you have DirectTV, which I do.

This correct.
 
> Mostly I just want first few things that I mentioned all built around an intuitive menu driven interface.  I want to build a theater room in my home and use this for watching movies and and pipe music of my choosing throughout my house.

You won't be able to pipe music around your home but you can play music at each frontend.
 
> 2.  How difficult will this be to setup?  I work in IT and have access to a couple of people who I WOULD consider Linux experts.

If you do not have linux and mythtv experience, it will be a time consuming project as if anything that you start to learn.

> 3.  Please explain the server and client configuration.  I would like to do this with a minimal amount of hardware.  Will I need a client and server?  If I go this route can the client operate over a wireless network and perform well?

Mythtv uses a frontend which is the UI and a backend that records tv. You can have multiple frontend per backend and have a frontend on the same computer as the backend. Also you can have multiple backends but only one master backend. Some people have used wireless N but mythtv doesn't stream video. So you might get hiccups when viewing.

> 4.  I want to build this thing right, so is there a hardware compatibility list that I can follow to get the best of the best hardware?

Review this post: [http://ubuntuforums.org/showthread.php?t=566529]("http://ubuntuforums.org/showthread.php?t=566529")

---

### Post by Bucky Ball on 2009-09-17
> **oldsoundguy said:**
> start here:

[http://www.mythbuntu.org/installation_manual](http://www.mythbuntu.org/installation_manual)

then put mythbuntu into Google and have at it.  Especially the Mythbuntu Forum!
Just like this Ubuntu forum, you will find some really knowledgeable peeps there that understand that not everyone is born knowing everything about computers and they will, as does this forum, answer your questions.  Just be sure to get the question into the title of your thread as that will garner not only MORE responses, but quicker responses.
+1

Top advice as usual oldsoundguy. rdhaines, get as specific as possible ...

---

### Post by tgm4883 on 2009-09-17
> Recording and watching live TV is secondary to me, although it would be nice. I'm told this is next to impossible if you have DirectTV, which I do.
[QUOTE]This correct.[/QUOTE]

Not exactly, I was able to do it just fine for about a year. It wasn't HD, but I captured widescreen on my PVR-500 with multiple tuners just fine. You need a box for each tuner though and a way to change the channel. I used serial/usb cables for that.


> Mostly I just want first few things that I mentioned all built around an intuitive menu driven interface. I want to build a theater room in my home and use this for watching movies and and pipe music of my choosing throughout my house.
[QUOTE]You won't be able to pipe music around your home but you can play music at each frontend.[/QUOTE]

Sorta. No, you won't be able to just pipe music directly from MythTV without some additional hardware (and really, it won't be through MythTV anyway). I would suggest either getting a amplifier that will do that for you and using mythtv as one of the sources, or just using the frontends (although they won't be in sync).

---

