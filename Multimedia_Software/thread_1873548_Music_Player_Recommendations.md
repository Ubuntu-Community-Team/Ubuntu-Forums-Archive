---
title: "Music Player Recommendations?"
date: 2011-11-01
forum: Multimedia Software
---

### Post by KelinciHutan on 2011-11-01
I know, there are a lot of these threads already, but after browsing through the search results, I came to the conclusion that the most effective way to get an answer to this question in my particular case was to go ahead and ask it again anyway.

So, I am a super-new Ubuntu user (as in, I installed it yesterday and I've never used Linux before in my life), and I've got my mp3s and DVDs playing and everything, so that's all fine.  However, up to now, I've used RealPlayer for playing music, despite the fact that it's slow and irritating, because it was crazy easy to make/manage playlists in it.  I am looking for a media player with similar playlist management, but that will hopefully not be quite so slow as RealPlayer was.  I keep my music fairly well organized, so getting album art/other metadata stuff is not a priority.  Nor is it necessary for me to find a music player that also plays DVDs/other media files, since I use VLC for those things (I hate the way VLC handles playlists or else I'd be using it for music, too).  So basically, I'm just looking for something that makes playlists really easy to make and keep organized the way I want.

Any suggestions?

---

### Post by 2F4U on 2011-11-01
Why not use the default audio player that comes with Ubuntu? Do you have any problems with it?

---

### Post by Lars Noodén on 2011-11-01
> **KelinciHutan said:**
> Any suggestions?

You could look at [Clementine](http://www.clementine-player.org/).  It's written in C++.

---

### Post by KelinciHutan on 2011-11-01
> **2F4U said:**
> Why not use the default audio player that comes with Ubuntu? Do you have any problems with it?
Not specifically.  I haven't had any difficulty getting it to work, if  that's what you mean.  And it could very well be I've missed some of the  features in it, since I'm still "moving in," so to speak.  But if there  is a better program for doing this, I guess I'd just hate to not know because I  didn't ask.

---

### Post by cbowman57 on 2011-11-01
> **Lars Noodén said:**
> You could look at [Clementine]("http://www.clementine-player.org/").  It's written in C++.

I second that, Clementine is great.

---

### Post by tartalo on 2011-11-01
I would recommend Amarok. It's bloated but well designed.

Clementine is a fork of the old Amarok, also a good recommendation.

Audacious is lighter and allows several playlists but doesn't have a media library.

Finally, Foobar2000 works under Wine.

> **2F4U said:**
> Why not use the default audio player that comes with Ubuntu? Do you have any problems with it?

Maybe the problem is that Banshee (as Rhythmbox, or Quodlibet, or many others) mix the media library and the playlist, and the main playlist changes everytime you navigate through your library.

That sucks, say that while you are listening to an album by Coldplay you want to have a look at the albums yo have by Iron Maiden, Coldplay song ends while you are browsing the library  and BANG! sudenly Satan is in the room.

So if you want any control you need to use a playlist anyway, only problem is that Banshee (and Rhythmbox etc) don't consider the playlists a priority and don't allow you see the media library and the playlist contents at the same time, so building a playlist is unnecesarily tedious.

Quodlibet developers have realised about this problem so they have given playlist-like superpowers to the queue, but that's a bad solution, because elements dissapear from a queue, as they should in a queue, but not in a playlist.

---

### Post by ballantony on 2011-11-01
Amarok never quite worked for me under 11.04 and Unity.  It was always a fiddle to get the menus to display properly.  In the end I went for Banshee.  It's good enough

---

### Post by dniMretsaM on 2011-11-01
Here's a short list of some FLOSS media players:
[QUOTE=Tech-Freedom]
Amarok - [http://amarok.kde.org/](http://amarok.kde.org/) Banshee - [http://banshee.fm/](http://banshee.fm/)
Clementine - [http://www.clementine-player.org/](http://www.clementine-player.org/) 
Exaile - [http://www.exaile.org/](http://www.exaile.org/) 
gmusicbrowser - [http://gmusicbrowser.org/](http://gmusicbrowser.org/) 
Guayadeque - [http://sourceforge.net/projects/guayadeque/ ]("http://sourceforge.net/projects/guayadeque/%20")
Miro - [http://www.getmiro.com/](http://www.getmiro.com/) 
Rhythmbox - [http://projects.gnome.org/rhythmbox/](http://projects.gnome.org/rhythmbox/)
Xnoise - [http://www.xnoise-media-player.com/](http://www.xnoise-media-player.com/) 
[/QUOTE]

I personally use Amarok. Miro is a little slow, so you would probably prefer something else.

Also, RealPlayer has a GNU/Linux version, but I can't recommend installing it because it's a proprietary application.

---

### Post by haqking on 2011-11-01
Clementine is great and so is Deadbeef (very low resources)

---

### Post by tartalo on 2011-11-01
> **haqking said:**
> Deadbeef (very low resources)

Deadbeef is not in the repositories, but has a PPA:

```
sudo add-apt-repository ppa:alexey-smirnov/deadbeef
sudo apt-get update
sudo apt-get install deadbeef
```

---

### Post by haqking on 2011-11-01
> **tartalo said:**
> Deadbeef is not in the repositories, but has a PPA:

```
sudo add-apt-repository ppa:alexey-smirnov/deadbeef
sudo apt-get update
sudo apt-get install deadbeef
```

ahh yah good point.

great player, definatley worth a look and i love the 25mb or less resources

---

### Post by KelinciHutan on 2011-11-01
Woot!  Thank you all for the awesome recs.  I'll give these a try and see what works out.

Very much appreciated.

---

