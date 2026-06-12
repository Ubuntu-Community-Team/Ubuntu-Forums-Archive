---
title: "What do I need JACK for?"
date: 2011-03-08
forum: Multimedia Software
---

### Post by valacirca on 2011-03-08
I'm an ubuntu noob and I installed a copy of 10.10 today.

The first thing I wanted to do was get my Behringer UCA202 USB sound card to work because the sound was initially coming out from the laptop speakers and not through my bookshelf speakers via the USB sound card. It didn't occur to me outright to fiddle with the sound preferences, but that's what eventually solved my problem. I just picked the correct device in the sound preferences and everything was fine.

My question is actually related to what I did *before* I solved the problem. Before actually trying the obvious solution, I found myself researching about audio for ubuntu, which led me to JACK, which I wasn't able to configure properly. My question is: What exactly do I need JACK for? If I'm able to use my USB speakers and play audio and video fine with it, what's the purpose of setting up JACK?

---

### Post by Kirboosy on 2011-03-08
You need JACK for fixing a flat tire on your car...:lolflag: JUST KIDDING


> 
**[What is JACK?]("http://jackaudio.org/node/11")**

                  Have you ever wanted to take the audio output of one piece of software  and send it to another? How about taking the output of that same program  and send it to two others, then record the result in the first program?  Or maybe you're a programmer who writes real-time audio and music  applications and who is looking for a cross-platform API that enables  not only device sharing but also inter-application audio routing, and is   incredibly easy to [learn and use]("http://jackaudio.org/files/docs/html/index.html")? If so, JACK may be what you've been looking for.  
  JACK is system for handling real-time, low latency audio (and MIDI). It  runs on GNU/Linux, Solaris, FreeBSD, OS X and Windows (and can be ported  to other POSIX-conformant platforms). It can connect a number of  different applications to an audio device, as well as allowing them to  share audio between themselves. Its clients can run in their own  processes (ie. as normal applications), or can they can run within the  JACK server (ie. as a "plugin"). JACK also has support for distributing  audio processing across a network, both fast & reliable LANs as well  as slower, less reliable WANs. 
 
 JACK was designed from the ground up for professional audio work, and  its design focuses on two key areas: synchronous execution of all  clients, and low latency operation. More [background information]("http://jackaudio.org/documentation") is available. 
 **Understanding JACK in different ways**

[Jack Homepage]("http://jackaudio.org/")

Essentially if you are a DJ or someone who works with audio, that is when you will need JACK. If you don't do much audio work I wouldn't worry about it to much. :)


~Caboose

---

### Post by valacirca on 2011-03-09
Thanks for that bit of info :) Actually, I do work with audio since I record music.

On Windows 7, I used to do it on Reaper.

Hopefully I could find an efficient DAW for Ubuntu :) [and be able to setup JACK properly as well]

---

### Post by cchhrriiss121212 on 2011-03-09
Reaper is actually one of the few DAWs that work well under Wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=21528](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21528)

But you will still need jack of course. If you want to try something made for Linux, try out Qtractor.

---

### Post by Kirboosy on 2011-03-09
Silly me. I forgot...

Welcome to the Forums! :D

I can't believe I didn't notice that was your first post...


Glad I could help. As to how you use/manipulate JACK I have no idea, but I know some people on the forums can help. :)


~Caboose

---

