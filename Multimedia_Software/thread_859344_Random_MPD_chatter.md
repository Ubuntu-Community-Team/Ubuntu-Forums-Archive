---
title: "Random MPD chatter"
date: 2008-07-14
forum: Multimedia Software
---

### Post by chochem on 2008-07-14
Seeing as I didn't find any major mpd threads out there, I figured I'd try creating creating a thread like [the one on Openbox]("http://ubuntuforums.org/showthread.php?t=190476"), collecting various [MPD]("http://www.musicpd.org/") titbits and lore. Hopefully other MPD fans out there will pitch in with questions and or share setups, ideas etc. 

Just to kick things off: I'm kinda missing a good database browser program, especially one that'd allow me to browse albums by cover (probably more like [quod libet]("http://www.kitenet.net/~joey/blog/pics/ql.png") than [cover flow]("http://www.applecart.co.za/itunes/images/coverflow_hero_mac20060912.jpg")). MPD/MPC/My own bash scripts/Sonata is fully sufficient when I know what I want but to explore the darker corners, I'd prefer something else. Any ideas?

---

### Post by urukrama on 2008-07-14
> **chochem said:**
> Just to kick things off: I'm kinda missing a good database browser program, especially one that'd allow me to browse albums by cover (probably more like [quod libet]("http://www.kitenet.net/~joey/blog/pics/ql.png") than [cover flow]("http://www.applecart.co.za/itunes/images/coverflow_hero_mac20060912.jpg")). MPD/MPC/My own bash scripts/Sonata is fully sufficient when I know what I want but to explore the darker corners, I'd prefer something else. Any ideas?

Have you seen [MPDBrowser]("http://www.gnomefiles.org/app.php/mpdBrowser")?

If you'd rather stick with Sonata, do you know you can set the default view in the 'Library' tab to 'Album' (click on the artist icon in the lower left corner and select album)?

---

### Post by chochem on 2008-07-14
Thanks urukrama, you're a treasure trove of information :) 

I didn't know about mpdbrowser and it hits the spot perfectly. It obviously can't stand alone and probably isn't meant to, but I think it'll complement Sonata very well. Took a bit of time installing from source and setting it up (strange that you have to tell it what your mpd music directory is in order for it to find the covers - surely that information could be gleaned from the mpd configuration) but I figured it out.

And I didn't know either that Sonata did have a proper database browser. Thanks for pointing it out. Of course it doesn't equal mpdbrowser in sheer coverlistic glossy glee but still handy.

---

### Post by eriqjaffe on 2008-07-14
As MPD clients go, GMPC is my one of choice.  I liked Ario as well, but I just kept going back to GMPC.

---

### Post by urukrama on 2008-07-15
> **eriqjaffe said:**
> As MPD clients go, GMPC is my one of choice.  I liked Ario as well, but I just kept going back to GMPC.

Me too. I love GMPC! I liked sharpmusic, a client written in C# that looked like Muine, but I haven't been able to compile it on any system since Breezy (if I remember correctly). Too bad it is no longer developed.

---

### Post by chochem on 2008-07-15
gmpc just looks so plain to me. It does have an impressive array of ways to add music to the playlist but for that I'd rather go with either 100% CLI (bash scripts) or 100% GUI (such s mpdBrowser). Sonata isn't impressive in that regard but it's simple and stylish and gives me an overview and that's all it's there for. The beauty of mpd and the best clients IMO is that they exemplify 'Do one thing and do it well'.

---

### Post by urukrama on 2008-07-15
It's funny that you don't like gmpc because it is plain, but that you say the best clients "exemplify 'Do one thing and do it well'." :p (Sorry, I couldn't resist)

I like GMPC's interface (the "Collapsed Interface" with the browser, not the default interface). And it has some nice touches: you can right click on the osd to get play/payse and next/previous buttons to change or stop the current song; you have a nice "Song information" window, that can display the lyrics and cover art, but also other albums by the same author. Its Tab browser can be pretty useful too, if you set it up in the Preferences window.

I rarely use some of its windows (Metadata browser and Database search). But the ones I do use I like. And GMPC always ran lighter on this computer than Sonata did (with previous releases of Sonata, the difference was very substantial!).

But to each his own. :D

---

### Post by qball on 2008-07-17
new gmpc coming soon.. 0.15.5 for hardy is on my ppa btw.

---

### Post by chochem on 2008-07-18
> **urukrama said:**
> It's funny that you don't like gmpc because it is plain, but that you say the best clients "exemplify 'Do one thing and do it well'." :p (Sorry, I couldn't resist)

Is there a contradiction? Or are you just pointing out that I should be lauding gmpc for being good at being ugly ;)

Anyway... I set up [relaxxplayer]("http://relaxx.dirk-hoeschen.de/index.php#") - a web interface to mpd - on my laptop. It works very well in the sense that I can access mpd and give it orders and such from the laptop itself or anywhere else on the web. Only... I'm not sure if I've got the wrong end of the stick here: I figured that a web interface included the idea of streaming the output to the pc where I was accessing the relaxx interface. That however still eludes me. I press play, and crank up the volume both on the local pc and on mpd but i can't hear a peep.

Have I misunderstood the concept? Are mpd-web interfaces just a big, ugly remote that I can use to annoy my neighbours with when I'm not at home (playing 'Ace of Spades' for them at 6 in the morning without hearing any of it myself)? Or is it just a two-pronged assault: one involving controlling the player, the other involving a way to attach the local pc to my "server's" audio output?

---

