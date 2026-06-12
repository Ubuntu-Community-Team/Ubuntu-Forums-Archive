---
title: "How can I record a LastFM stream to Mp3?"
date: 2009-05-17
forum: Multimedia Software
---

### Post by w.g.hanna on 2009-05-17
I'd like to record lastfm streams to mp3.  I'm running Hardy. 

I've tried a number of routes to do this.  

Attempt 1:  [http://www.linuxmonitor.net/blog/2007/03/ripping-mp3s-from-lastfm-with-linux.html](http://www.linuxmonitor.net/blog/2007/03/ripping-mp3s-from-lastfm-with-linux.html)

The problem was i didn't really understand the instructions.  Were those terminal commands?  Or are they text files - a process I've enver really understood.  At any rate, I found both the lastfm proxy and streamripper in synaptic.  so i installed, but I can't find either in my application list.  

Attempt 2:  [http://thelastripper.com/](http://thelastripper.com/)

I successfully installed the deb and its listed in my applications.  when i run it two windows pop up.  one is titled preferences, the other is titled the last ripper.  i can't do anything with the last ripper window until i enter my lastfm username and password and set a music directory.  Then, theoretically, I can enter a lastfm station into the other window. the last ripper help page suggests i need to put it in this format:  lastfm://globaltags/pop.  however, when i do that, it just seems to hang  -music never starts - and it never starts recording.  

Attempt 3:  Rhythmbox add on.

In the add on section of Rhythmbox there seems to be an application that lets you record lastfm streams.  However, I can't even get lastfm to play in rhythmbox, let alone record.  All i get is a window that pops up saying:

Problem occurred without error being set. This is a bug in Rhythmbox or GStreamer.

Attempt 4:  Amarok add on.    

Never been a big fan of Amarok.  For whatever reason, the program runs slow on my computer - regardless whether the session is gnome or kde.  whatever.  Whatever- if it'll do what i want, i'll use it.  but again, i can't get lastfm to play - all i get is an error screen - 

Error Loading Media
No suitable input plugin. This often means that the url's protocol is not supported. Network failures are other possible causes.
[http://195.24.233.49:80/last.mp3?Session=5873ac77e14f18754b412f69577729a4](http://195.24.233.49:80/last.mp3?Session=5873ac77e14f18754b412f69577729a4)

So that's where I'm at.  I plan on updating my OS soon - but this was my first linux, and i'm a little trigger shy.  i want to take the time to sort out all my files and just start over.  so i suppose there's always a chance that if nobody can help me get it going in hardy, jaunty might just work.  Any help is appreciated.

---

### Post by w.g.hanna on 2009-05-17
bump

---

### Post by tgalati4 on 2009-05-17
Install vagalume and play an artist.  See if lastfm is working correctly.

If so, then you need a proper URL to feed into thelastripper.

You can use the bookmark feature in vagalume to cut and paste.

For example, I'm listening to Dave Grisman:

lastfm://play/artists/1024280

RE: method 1, that's from 2007.  My sundial tells me it's 2009.  Things change. The basic procedure looks correct, but the scripts may not work as lastfm is a moving target.

---

### Post by andrew.46 on 2009-05-18
Hi w.g.hanna,

This can usually be done quite easily with either vlc or MPlayer. Can you give an address of a typical stream from this site that you would want to record? I would be happy to have a look and see if I can both save the stream and demonstrate an easy  way to do it :-).

All the best,

Andrew

---

### Post by mc4man on 2009-05-18
Andrew
On my way to bed, small note
For last fm streams you need to sign up first (username, password ect.
[http://www.last.fm/](http://www.last.fm/)

---

