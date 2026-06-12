---
title: "dumb question - what exactly IS streaming?"
date: 2014-08-18
forum: Multimedia Software
---

### Post by dave131 on 2014-08-18
I'd like to build a cheap (hopefully) box to be able to keep movies, etc., on.  I've read the term "streaming" in many many threads and internet posts on this, but just not sure exactly what that means.  Running my Raspberry Pi as a media center, connected to my TV but also accessable via the local network, is that streaming?

I'm thinking of building this cheap box as I *thought* streaming would be something like having Ubuntu server running and being able to access media files - music, movies, etc. - from other boxes in the house.  It would give me a chance to *gulp*  *try *to learn a little about a server (I know nothing) and also running something on it for media access.  

As you can see, I don't know anything about this.  I see wi-fi enabled TV's, Blue-ray players, etc., and don't know if I set up an Ubuntu server if I could somehow access the movies, etc., from it on one of those devices.

Can you help out an extremely confused guy? ;)

---

### Post by yancek on 2014-08-18
An online search for 'what is video streaming' will provide you with a lot of results such as the definition below:

> Streaming media is multimedia that is constantly received by and  presented to an end-user while being delivered by a provider. Its verb  form, "to stream", refers to the process of delivering media in this  manner; the term refers to the delivery method of the medium rather than  the medium itself. ...

---

### Post by dave131 on 2014-08-18
But WHAT can be the "provider" and WHAT can be the "end-user"?   I've read many things on the net already, but asked here because I'm still confused.  A little help instead would be appreciated.  Can the provider be SOMETHING (I don't KNOW what) running on an Ubuntu server?  Can the end-user be a wireless-enabled TV, a wireless-enabled blue-ray, my tablet?  What software would be possible to use on an Ubuntu server to "stream"?  Is special software required at the end-user?

EDIT: perhaps to clarify a little more:  when I think of streaming as we used the term many years ago, "something" was constantly broadcasting, and you could connect or listen in on that stream.  Does the "provider" have to be constantly just broadcasting something, or does the end-user have a way to select what is streamed?  Again, what software?  How?

---

### Post by yancek on 2014-08-18
How to use it with vlc at the site below...

[http://www.howtogeek.com/118075/how-to-stream-videos-and-music-over-the-network-using-vlc/](http://www.howtogeek.com/118075/how-to-stream-videos-and-music-over-the-network-using-vlc/)

---

### Post by QIII on 2014-08-19
OK, folks.

I've edited the last two posts for a bit of snarkiness each.

Keep it civil and polite.

---

### Post by JDorfler on 2014-08-19
You can install MediaTomb on your box, then on your Pi install VLC.  You can then watch/listen/look at your Movies, Pictures, and Music from your Server on your TV.

---

### Post by dave131 on 2014-08-19
So, I run Ubuntu server, install something like mediatomb, xbmc, etc., then have a program at the other end capable of interacting with that program on the server to select and play media?  Does this mean that a wireless blue-ray or wireless TV have some sort of software on them to interact with a program on a server?  If so, what is the program on the server that would interact directly with a wireless blue-ray or wireless TV?  In other words, if the blue-ray and/or TV is wireless enabled (I *assume* that mean 802.11) and I don't want any extra hardware (such as the Pi) between the server and the blue-ray/TV, will that work, and what are the software requirements at each end?

Thanks for the reply.

---

### Post by dave131 on 2014-08-19
Ok, armed with the above suggestions, I've gone back to the threads here and on the net in general and re-read the streaming to a TV/blue-ray threads.  Am I understanding correctly that I can't go directly to those devices?  That I need something in between - such as a media extender of some sort (hence the Pi suggestion by jdorfler) that can receive LOCAL wifi network data and direct connect to the blue-ray or TV?  I'm also assuming that the TV must have the ability to send remote control button presses back down the HDMI cable (I don't remember what that's called, but I know my TV doesn't do it).  If so, do all newer TV's with HDMI support that now?

Thanks.

---

### Post by dave131 on 2014-08-19
Oh, and another question on this:  is it possible for more than 1 TV with a media extender such as a Pi to access media on the server via the MediaTomb software you mentioned?

Thanks.

---

### Post by dave131 on 2014-08-19
Ah.....so it works via uupn or uupp or whatever it's called?  So I could actually be running XMBC on a Pi at the user end, using my normal multi-device remote via a USB IR receiver at the Pi, and just direct XMBC to the uupp/uupn/whatever as the source??   That would make things easy - I would keep using a Pi, keep running XMBC, but with no need for a local hard disk at the Pi.  So the Pi is fast enough to receive a media stream via wireless and play it via the HDMI to my TV without lag or "weird" stuff happening?

I'm trying to understand all of this, so if I have any of this wrong please stop me now and correct me before I get too excited!

Thanks!

---

