---
title: "Which music player for a fairly big library?"
date: 2009-10-25
forum: Multimedia Software
---

### Post by Pott on 2009-10-25
I have 9,000 songs on my PC, all MP3s. 

I use Media Monkey and MP3Tags on Windows to manage everything.
I tried Exaile and Rythmbox on Jaunty but it's all very slow and the hotkeys don't work (though I think that's yet another issue...)

So I want a player that's comfortable dealing with a very large library, coming from an external HDD. I don't need podcast support, playlists functions or anything. I usually just put the entire libary on shuffle and go from there.

I am NEVER at my PC without music being played and it's a big gap when I use Linux :( I hope there's something out there...

Thanks!

---

### Post by Keith Hedger on 2009-10-25
I've got some 6000 song files in my library and I use quod libet (it's in the repos), I've found it very stable and capable

---

### Post by mcduck on 2009-10-25
MPD is always a good choice. Just pick the client(s) you like most. I use Sonata & ncmpcpp.

Handles my ~10 000 song library better than anything else I've ever tried. (plus all the benefits of running the music player as a daemon, like being able to start playing a playlist, closing the client and music still playing. And the player continuing from where it left when I start the computer, even before I log in to the desktop..)

---

### Post by Pott on 2009-10-25
What's MPD? Is it in the Add programs function? I'm not quite sure what a client is either... 

Can I just do a sudo apt-get MPD?

---

### Post by vinutux on 2009-10-25
Try Banshee or Youki [new one ]

---

### Post by mcduck on 2009-10-25
> **Pott said:**
> What's MPD? Is it in the Add programs function? I'm not quite sure what a client is either... 

Can I just do a sudo apt-get MPD?

[http://en.wikipedia.org/wiki/Music_Player_Daemon]("http://en.wikipedia.org/wiki/Music_Player_Daemon")
[http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki]("http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki")

Basically MPD runs as a background service on your computer, playing your music. It can be then controlled through many different applications, which don't even have to run on the same machine (and which don't of course need to be even running for the music to play).

This means that you'll get a lightweight music player with a good and fasrt library, and then can still change between different clients to find one you like most (without having to actually create a different music library etc. in each player, since it's always MPD that handles the library and plays the music).

MPD is in the repositories, but it takes a bit of configuring to get it working (although not much, a couple of terminal commands is in most cases enough to get it working). And of course you'll also need some client program for controlling MPD.

---

### Post by Pott on 2009-10-25
Thanks I think I'll give it a try! Do you know what's the most basic, fuss free client that includes album art? I just want something fast and simple... I'm considering Ario for now.

Thanks for the suggestions people, keep them coming if you have more :)

---

### Post by meho_r on 2009-10-25
> **Pott said:**
> Thanks I think I'll give it a try! Do you know what's the most basic, fuss free client that includes album art? I just want something fast and simple...

Thanks for the suggestions people, keep them coming if you have more :)

Strange nobody mentioned [gmusicbrowser](http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html). IMHO by a clear mile the best music player ever :) It beats too easily its competition when power and speed are at stake. Ideal for managing large libraries (10.000+), has advanced filters, you can even navigate through songs using popup (tray tip), highly customizable... Definitely worth a try.

However, be warned, can be confusing at first sight (fast, but not so simple), but after playing a little and setting layout of your preference, you will never search for a music player again ;)

---

### Post by Pott on 2009-10-25
Thanks, that sounds like what I'd want. Unfortunately I read the instructions for installation and it's nothing I know how to do :( It says I need a bunch of things already which I'd have no clue how to get, and I generally don't know how to deal with these things yet, I've only had Ubuntu for about two days... 
To be honest MPD doesn't seem any easier to get running either, along with the client...

---

### Post by meho_r on 2009-10-25
Just go to Download section and pick up .deb file (gmusicbrowser_1.0.2_all.deb). After downloading it, for installation double click on the file, enter your password when requested and that's it. If any additional files are needed, they will be installed automatically. You'll find gmusicbrowser after installation in Applications > Sounds&Video.

If this doesn't work for some strange reason, you can install it from repos (although an older version). System > Administration > Synaptic Package Manager, after that search for "gmusicbrowser".

---

### Post by mcduck on 2009-10-25
> **Pott said:**
> Thanks I think I'll give it a try! Do you know what's the most basic, fuss free client that includes album art? I just want something fast and simple... I'm considering Ario for now.

Thanks for the suggestions people, keep them coming if you have more :)

Sonata is excellent client with support for both album art & lyrics.

If you haven't got MPD runnning yet, here's how I recommend doing it:

First, install everything required:
```
sudo apt-get install mpd mpc ncmpc sonata
```

Next, you'll want to link your music directory into MPD's default music directory:
```
sudo ln -s /path/to/your/music /var/lib/mpd/music
```
If you have multiple locations where you have music files you can also link them as subdirectories instead of linking them directly to /var/lb/mpd/music itself. Also removable drives work just fine, but you'll want to make sure the drive is mounted in the same location every time you plug it in, so you might want to label the drive or configure it in fstab. Also you don't want to update your MPD library if the drive is not plugged in..

Finally, all you need to do is open the client and update the library. You can also use MPC to do that, by running this:
```
mpc update
```

That's it. Once the library update has finished you'll be ready to start using it. If you need to, MPD's configuration file is /etc/mpd.conf. There are some options for sound output, file & ID3 tag encodings etc, but the defaults will work just fine in almost all cases. And you'll find Sonata in Applications/Sound & Video/Sonata.

---

### Post by Pott on 2009-10-28
Thanks! I went with gmusicbrowser + mpg321 and everything works pretty well.

---

### Post by vinutux on 2009-10-28
> **Pott said:**
> Thanks! I went with gmusicbrowser + mpg321 and everything works pretty well.

plz...mark thread SOLVED under [COLOR="Red"]**thread menu**[/COLOR] [top right]

---

### Post by ufugu on 2009-10-28
FWIW I have 22,000 tracks (mostly ripped from 78s believe it or not)and although I have never found the perfect music player, library speed has not been a problem in any recent player after the initial library scan. 

You sure it's not something else?

Sorry, solved, never mind.

---

