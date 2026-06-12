---
title: "MPD advantages ?"
date: 2010-02-23
forum: Multimedia Software
---

### Post by yocec on 2010-02-23
In order to chose my music player, I'me looking at MDP client/server system.

But I can't understand what is the advantages of this client/server architecture over a classical music player (like rythmbox, atunes, amarok) which access the network music over a NFS/SMB share ?

For information if I chose MPD I will not use a command line MPD client but something like Sonata


Thanks for answers
Yoann

---

### Post by TenPlus1 on 2010-02-23
I prefer using MPD and the gui called Xfmpc for my music needs because it's a lot faster at cataloguing my music library and uses less resources than most music players...  I can easily output my preferred audio to my speakers or across a network/streamcast...

Xfmpc is a simple and small front-end for MPD although Sonata and Gmpc have more features...  I also like being able to log out and having the music still playing :)

This may help: [http://mpd.wikia.com/wiki/Configuration](http://mpd.wikia.com/wiki/Configuration)

---

### Post by yocec on 2010-02-24
Thanks for the answer

---

### Post by mcduck on 2010-02-24
* lightweight

* can be controlled through network (for example I use my Android phone as remote controller)

* many different user interfaces which you can use as you like without having to import your music into many different programs

* runs as it's own user, so it doesn't depend on being logged in or having the client open. If you leave it playing and shut down the computer it will start playing automatically from where it left before you even get a change to log in (great if you have a dedicated music server that you don't use as desktop machine)

* when combined with a streaming server & web server makes all your music accessible from anywhere, even through Internet (without having to install any special software on the machine you use to connect to the server, web browser and any music player capable of playing internet radio is enough)

* excellent library that handles large music collections easily

* command-line clients and programming libraries allow some interesting solutions, for example I have MPD controls, playlists and library contents directly in my Openbox menu

* did I mention lightweight? ;)

---

### Post by yocec on 2010-02-25
Many thanks for these complete answer.

One more question, can we change track tag's throught the MPD client ?
Is there a client or is MPD server handle track rating into popularimeter ID3 tag ?



> * lightweight
good point


> * can be controlled through network (for example I use my Android phone as remote controller)
Don't actually need it


> * many different user interfaces which you can use as you like without having to import your music into many different programs
don't neeed it at the moment, but usefull


> * runs as it's own user, so it doesn't depend on being logged in or having the client open. If you leave it playing and shut down the computer it will start playing automatically from where it left before you even get a change to log in (great if you have a dedicated music server that you don't use as desktop machine)
Good point

> * when combined with a streaming server & web server makes all your music accessible from anywhere, even through Internet (without having to install any special software on the machine you use to connect to the server, web browser and any music player capable of playing internet radio is enough)
Good point

> * excellent library that handles large music collections easily
5000 tracks = large music collection I don't think

> * command-line clients and programming libraries allow some interesting solutions, for example I have MPD controls, playlists and library contents directly in my Openbox menu
Need to digg it


> * did I mention lightweight?
No ?


Thanks again

---

### Post by mcduck on 2010-02-25
Yes, it's possible to edit ID3 tags if the client you use supports that. ncmpcpp (CLI client) has excellent tools for adjusting tags on large number of files easily, but I remember Sonata having basic tagging options as well. Probably many other clients also have that.

I have no idea about popularimeter tags, first time I even hear of such thing ( I had to google it to find out what you are talking about :D). If that's possible. it would be a feature of some client and not MPD itself (as far as I know MPD will write any tag if the client just tells it what to do).

..oh, I almost forgot:

* gappless playback of MP3, OGG and FLAC files (seems to be a huge problem for surprisingly many players). There's also crossfading if that's what you want.

---

### Post by yocec on 2010-02-26
I will try.

I know and use popularimeter because mediamonkey music library organiser software use it.
So my music is partially rate with this.

I think itunes use it to (but I don't care)


The problem with popularimeter is that tag allow numeric value from 0 to 255 so even if 2 software use it they probably don't use the same intervals for the star rating...

This will need standard...

---

