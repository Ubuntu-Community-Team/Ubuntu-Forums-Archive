---
title: "Best music streaming setup"
date: 2009-06-11
forum: Multimedia Software
---

### Post by HDave on 2009-06-11
I've been a long time Ubuntu user (both server and desktop), but am a totaly newbie to audio streaming.  I have a large collection of music files on a server and would like to stream them to a variety of clients both on the LAN and over the internet.  Ideally I could do this without requiring a specific player on the client.

Whats the best way to do this?  I am wondering about both the server-side and the client side as well.

---

### Post by andersbk on 2009-06-11
Well. You're always going to need a specific client to play the stream or file.

I really like MPD [http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki](http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki)
But that's a server side player. Nice for a home setup where your server plays the music through your home system, but control can be remote.

For actual streaming look into shoutcast/icecast.

Also there's a couple of web based tools that work well. i.e.:

[http://ampache.org/](http://ampache.org/)
[http://en.jinzora.com/](http://en.jinzora.com/)

.

---

### Post by markbuntu on 2009-06-11
Setting up a shoutcast or icecast server would probably be the easiest since you want to stream to the internet. Clients can use almost anything to recieve it.

---

### Post by HDave on 2009-06-11
Thanks guys, I'll check 'em out and report back.

---

### Post by HDave on 2009-06-12
> **andersbk said:**
> 
Also there's a couple of web based tools that work well. i.e.:

[http://ampache.org/](http://ampache.org/)
[http://en.jinzora.com/](http://en.jinzora.com/)

.

Jinzora looks pretty cool.  It does audio and video, has a slick GUI, and works with a myriad of clients and file formats.  Going to give it a try. Thanks.

---

### Post by HDave on 2009-06-12
> **markbuntu said:**
> Setting up a shoutcast or icecast server would probably be the easiest since you want to stream to the internet. Clients can use almost anything to recieve it.

These seem like they are internet streaming technologies and would not present the client user with a a selectable list of songs to choose from to play or make a playlist from. Rather they are used for making your own kind of radio station. Is this right?

---

### Post by markbuntu on 2009-06-15
Yes, that is pretty much what they do, stream a playlist. 

You should check out mediatomb if you want to set up a UPnP media server so people can access a song database with their web browsers or vlc or even windows media player.

---

### Post by HDave on 2009-06-30
Well I got Jinzora up and running and have to say it is pretty cool.  It works with both videos and music and looks very nice.  Thanks for the help.

---

