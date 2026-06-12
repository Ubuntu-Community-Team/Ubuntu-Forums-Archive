---
title: "Looking for a music player"
date: 2008-08-21
forum: Multimedia Software
---

### Post by Hitchhiker427 on 2008-08-21
Hey everyone.  If this isn't the best place for this thread, please move it for me.  Thanks.

I've been using Ubuntu on-and-off since Hoary (dual-booting with Windows), and in that time, I have yet to come across a music player that I'm satisfied with.  In Windows, I have several to choose from that I'm very happy with, Winamp being my absolute favorite.  There's a plethora of media software made for Linux, so surely there's *something* that meets my needs... right?

Anyways, I was wondering if I could list what I'm looking for, and get suggestions from the community concerning various music players that meet these requirements.

1)  I don't really care about video support.  I prefer to keep my music and videos separated, so although I don't mind if a music player can also play videos, it's not a benefit to me.

2) The player needs a decent media library organizer.  Programs like Winamp, iTunes, Amarok, and Banshee are all examples of a good media library.  This throws out XMMS and BMP as candidates.

3) Although I pointed to iTunes and Banshee as examples of having good media libraries, they do not handle playlists properly.  I absolutely *hate* music players that do not distinguish the media library from the playlist.  Winamp is my star example of separating the library from the playlist, however, Amarok does a good job of this as well.

4) Support for id3-tag embedded album art.  Also, the embedded art should ALWAYS take precedence over image files in the same directory.  Banshee handles this correctly, Amarok does not.  Amarok will simply ignore all embedded art if there happens to be an image file in the same directory.

5) Support for MTP media devices.  Banshee does this VERY well.  Amarok does it, but stability is glitchy.

6) Preferably an option to separate the player window from the media library/playlist.  Winamp and Amarok do this very well.  If the player does not support this, then maybe a 'mini-mode' like in Exaile or Banshee would be okay.

7) Preferably a GTK+ app.  Amarok, being a QT app, breaks all consistency and aesthetics of my lovely Gnome desktop.  However, Banshee and Exaile look great.

8) Lastly, the basics.  Low resource footprint, fast interface responsiveness, stable.  This rules out Amarok in my book, which has always been slowly and buggy (I've tried both the repository version and compiling from source... no luck).


So, any ideas?  I've been searching for quite some time, and cannot find a music player that works for me.  It seems that my biggest problem with Linux, and the main reason I keep Windows as my primary OS, is the simple lack of *quality* software that meets my needs.

Thanks in advance for any help.

---

### Post by carnagex420x on 2008-08-22
Take a look at Songbird, they are in the proccess of a new rollout now and its just a BETA but if not, in the meantime I would say Banshee is a good contender. Check this out too :  [http://www.makeuseof.com/tag/5-great-alternative-linux-music-players/](http://www.makeuseof.com/tag/5-great-alternative-linux-music-players/)

---

### Post by rainwalker on 2008-08-22
+1 for Songbird
I've also tried Exaile and Listen, both seem to be pretty good. Check them out and see if they're what you're looking for

---

### Post by kiran555 on 2008-08-22
hi everyone the music player is made up of linux software and it is very used to opparate.
================================================================
<a href="http://www.alcoholaddiction.org/alabama">
Alabama Alcohol Addiction Treatment</a>

---

### Post by kiran555 on 2008-08-22
hi everyone the music player is made up of linux software and it is very used to opparate.
================================================================

[URL="http://www.alcoholaddiction.org/alabama"]
Alabama Alcohol Addiction Treatment [/URL]

---

### Post by mrgnash on 2008-08-22
Have you checked out Banshee 1.2?

---

### Post by kpkeerthi on 2008-08-22
+1 for banshee 1.2. Install help for hardy is available [here]("https://edge.launchpad.net/%7Ebanshee-team/+archive")

EDIT: I've been using Banshee because it is the one that handles my iPod best in Linux. But I'm starting to feel that its getting overly bloated beyond my liking. MPD + Ario/Sonata, here I come!... But wait till I get RockBox for my iPod.

---

### Post by Hitchhiker427 on 2008-08-22
Wow, thanks for the replies everyone!  They're very appreciated.

A quick breakdown concerning some of the suggestions:

I've tried Songbird in the past and uninstalled it because I didn't like it.  So, I just went out and tried the newest version, and tried customizing it with extensions.  It's okay at best.  I like the fact that it's based off of the firefox source and is very extensible, but it just isn't for me.  It's just an iTunes clone with extensions.  I don't like the GUI inconsistency with the rest of my apps (although standalone, I must say Songbird is nice looking), and I really can't stand the iTunes-esque way of handling playlists.  Thanks for the suggestion, but it's really not what I'm looking for.

I have tried Exaile, and I really like it.  Except, it has virtually no features... which is kind of annoying.  Plus, it doesn't do embedded album art, and wouldn't work with my MP3 player.  The library/playlist organization is much better than that in Songbird/iTunes/Banshee, but not great.

Concerning Banshee, that was what I was using when I originally made this thread.  It did everything I wanted, except it organized the library/playlists that iTunes-eqsue way.  I can't possibly see how anyone can prefer that organization scheme, but whatever.  Banshee is an awesome program, except for that one show-stopper.  I really wanted to like Banshee, but just couldn't make myself.
EDIT: I want to add that I was referring to version 1.2, which is not in the repos.

Now, Listen is a player that I haven't tried in the past.  I must say, this is my new favorite.  So, thanks guys.  It does almost everything I want.  The only downside is that it doesn't seem to work with my MP3 player (MTP protocol).  However, the library/playlist organization is nearly perfect, and is the best I've seen in Linux yet.  It still does that annoying 'override embedded album art with random .jpgs' thing that Amarok does, but I can live with this.

So, thanks again for your recommendations.  It seems that Listen is the player for me.

---

### Post by mcduck on 2008-08-22
Apart from MTP support, I'd say MPD + a client of your choise would be the perfect solution. MPD doesn't support MTP, but some cklient might of course add suport for that as well. I don't know as I don't have any such devices (only ipod that I use with gtkpod).

---

### Post by rainwalker on 2008-08-22
> **Hitchhiker427 said:**
> Wow, thanks for the replies everyone!  They're very appreciated.

A quick breakdown concerning some of the suggestions:

I've tried Songbird in the past and uninstalled it because I didn't like it.  So, I just went out and tried the newest version, and tried customizing it with extensions.  It's okay at best.  I like the fact that it's based off of the firefox source and is very extensible, but it just isn't for me.  It's just an iTunes clone with extensions.  I don't like the GUI inconsistency with the rest of my apps (although standalone, I must say Songbird is nice looking), and I really can't stand the iTunes-esque way of handling playlists.  Thanks for the suggestion, but it's really not what I'm looking for.

I have tried Exaile, and I really like it.  Except, it has virtually no features... which is kind of annoying.  Plus, it doesn't do embedded album art, and wouldn't work with my MP3 player.  The library/playlist organization is much better than that in Songbird/iTunes/Banshee, but not great.

Concerning Banshee, that was what I was using when I originally made this thread.  It did everything I wanted, except it organized the library/playlists that iTunes-eqsue way.  I can't possibly see how anyone can prefer that organization scheme, but whatever.  Banshee is an awesome program, except for that one show-stopper.  I really wanted to like Banshee, but just couldn't make myself.
EDIT: I want to add that I was referring to version 1.2, which is not in the repos.

Now, Listen is a player that I haven't tried in the past.  I must say, this is my new favorite.  So, thanks guys.  It does almost everything I want.  The only downside is that it doesn't seem to work with my MP3 player (MTP protocol).  However, the library/playlist organization is nearly perfect, and is the best I've seen in Linux yet.  It still does that annoying 'override embedded album art with random .jpgs' thing that Amarok does, but I can live with this.

So, thanks again for your recommendations.  It seems that Listen is the player for me.

Told you it was good ;)

---

