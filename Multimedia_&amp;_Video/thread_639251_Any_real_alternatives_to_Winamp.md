---
title: "Any real alternatives to Winamp?"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by djbon2112 on 2007-12-13
Stupid question I know, probably been asked a billion times, but I love Winamp for it's media library; the layout, it's ability to access my iPod flawlessly, etc. Are there any media players that have a similar media library system, or a way to get Winamp working under WINE that actually allows the media library to open (I don't actually use many plugins so I could care less about that, though that seems to be the reason no one over there wants to develop Winamp for Linux *rolleyes*)

---

### Post by disturbedite on 2007-12-13
by the time winamp hit 5 i thought it was way too bloated.  the equivalent on linux is prolly audacious.  install it, try it, see what you think.  i love it.

---

### Post by markusf21 on 2007-12-13
I use exaile it's in multi-verse

---

### Post by awthomp on 2007-12-13
I'm a huge fan of Amarok.  I love the extra features like the Wikipedia search and lyrics.  Plus, it has a really intuitive feel, and I've never had any problems with it syncing with my iPod.

---

### Post by toupeiro on 2007-12-13
```
sudo apt-get install xmms<tab><tab>
```
Display all 104 possibilities? y/n 


:-)  there's your linux version of winamp, and more plugins than you can shake a stick at

---

### Post by djbon2112 on 2007-12-13
Wow that was quick!

I've tried XMMS, but I find it too much like iTunes and not at all like Winamp. Amarok I just installed, but it won't play MP3's... And I've got no idea how to fix that!

Trying the other two.

---

### Post by toupeiro on 2007-12-13
> **djbon2112 said:**
> Wow that was quick!

I've tried XMMS, but I find it too much like iTunes and not at all like Winamp. Amarok I just installed, but it won't play MP3's... And I've got no idea how to fix that!

Trying the other two.



xmms like itunes??? *gag*

I don't know what you saw, but if you think it looks like iTunes, I don't think it was XMMS.  xmms is pretty much a clone of winamp.

---

### Post by markusf21 on 2007-12-13
to get mp3 play back follow this [*[COLOR="Navy"]guide.[/COLOR]*]("http://www.psychocats.net/ubuntu/nonfree")

---

### Post by djbon2112 on 2007-12-13
> **toupeiro said:**
> xmms like itunes??? *gag*

I don't know what you saw, but if you think it looks like iTunes, I don't think it was XMMS.  xmms is pretty much a clone of winamp.

Alright then that wasn't the one I was thinking of, but it still lacks a media library! That's what I'm looking for, a good well-organized media library. I've got 110+ GB of music, and I need a good Artist -> Album -> Song organizational structure with search.

Oh, and Exaile isn't that bad, but it crashes every time I try to play a file.

---

### Post by toupeiro on 2007-12-13
> **djbon2112 said:**
> Alright then that wasn't the one I was thinking of, but it still lacks a media library! That's what I'm looking for, a good well-organized media library. I've got 110+ GB of music, and I need a good Artist -> Album -> Song organizational structure with search.

Oh, and Exaile isn't that bad, but it crashes every time I try to play a file.

I have roughly the same, but to manage the collection, I use amarok on a postgres database.  You'll be happiest there.

If bloat becomes a problem, XMMS2 has a media library and 100's of ways to interface with it.  It's also significantly more lightweight than amarok, but not as user friendily.  If you get frustrated with amarok, PM me and I will be happy to help you with XMMS2

---

### Post by awthomp on 2007-12-13
> **markusf21 said:**
> to get mp3 play back follow this [*[COLOR="Navy"]guide.[/COLOR]*]("http://www.psychocats.net/ubuntu/nonfree")

Amarok is KDE based and thus relies on the Kubuntu restricted dependencies (at least, this has been the case in my experience).

In 7.10

```
sudo apt-get install kubuntu-restricted-extras
```

I'm pretttttty sure that the Ubuntu restricted extras won't work in Amarok... but this may be due to the fact that I use the Xine engine rather than gstreamer.

---

### Post by djbon2112 on 2007-12-13
> **toupeiro said:**
> I have roughly the same, but to manage the collection, I use amarok on a postgres database.  You'll be happiest there.

If bloat becomes a problem, XMMS2 has a media library and 100's of ways to interface with it.  It's also significantly more lightweight than amarok, but not as user friendily.  If you get frustrated with amarok, PM me and I will be happy to help you with XMMS2

That's for the offer. I'm not a big fan of amarok's interface at present, and I still have no idea how to configure it, so I'm going to install XMMS2 right now and try it tommorow.

---

### Post by djbon2112 on 2007-12-13
Wow holy crap, sorry to repost so fast, but I just noticed Ubuntu's built-in Rhythmbox Music player. It's almost EXACTLY what I want from an interface standpoint. Now I just need to get it to play MP3s. I assume the process is the same as getting Amarok to play them, correct? I just need that in a simple guide :p

Just another question too, is there a way to move the Play queue to a different pane, and in general change its behavior? I don't like how if you click on a track it moves it to the top of the list. A playlist-like format (a la Winamp, of course! ;)) would be preferred!

------

I'm still interested in trying XMMS2 though, how do you get it installed? I've done...

```
sudo apt-get install xmms2
```

... like its homepage says but it's only 56 kb and there isn't a shortcut to it anywhere. Any advice?

---

### Post by awthomp on 2007-12-13
Yeah, for getting mp3s to play in Ubuntu (and thus Rhythmbox), the code should be:

```
sudo apt-get install ubuntu-restricted-extras
```

I'm not sure the exact way to install XMMS2.  Have you tried searching for it in Synaptic?

---

### Post by psusi on 2007-12-13
My God AOL really did bloat the crap out of winamp didn't they?  I still use a copy from before the kid sold to AOL from like 1998.  

Artist -> Album -> Song organization is just a directory tree, no bloated library software required.

---

### Post by djbon2112 on 2007-12-13
> **psusi said:**
> My God AOL really did bloat the crap out of winamp didn't they?  I still use a copy from before the kid sold to AOL from like 1998.  

Artist -> Album -> Song organization is just a directory tree, no bloated library software required.

Yea but my music is unorganized (mostly), and a lot of the apps don't even have that!

I don't find Winamp bloated though: the plugin system works both ways. I just remove the plugins for all the pointless crap in the media library until I have just my music, playlists and my iPod ;)

---

### Post by djbon2112 on 2007-12-13
> **awthomp said:**
> Yeah, for getting mp3s to play in Ubuntu (and thus Rhythmbox), the code should be:

```
sudo apt-get install ubuntu-restricted-extras
```

I'm not sure the exact way to install XMMS2.  Have you tried searching for it in Synaptic?

Just did... it says it's installed, and I installed all the plugins, but there's still no shortcut or anything to launch it!

---

### Post by disturbedite on 2007-12-13
ack, i don't know why anyone would use xmms any more.  its been dead for a long time.  audacious has replaced it.

---

### Post by Yellow Pasque on 2007-12-13
Last time I checked, Winamp (5.32?) ran fine under WINE for me (at least the basic stuff, not sure about shoutcast or stuff like that). I currently use foobar2000 under WINE though, for its better DSP plugins.

---

### Post by djbon2112 on 2007-12-13
5.5 barely runs, no media library, can't move stuff around, it's a pain.

As for Audacious, as far as I can tell, it doesn't have a media library feature, which as I said is the main thing for me right now.

---

### Post by psusi on 2007-12-13
> **djbon2112 said:**
> Yea but my music is unorganized (mostly), and a lot of the apps don't even have that!



A lot of apps don't have WHAT?  The operating system handles files and directories; you just name them appropriately when ripping.

---

### Post by SunnyRabbiera on 2007-12-13
well the latest winamp does work somewhat in wine under ubuntu.
but there are a few good alternatives to it:
Amarok: more of a itunes like app, but it does do well with ipods
Audacious: a great winamp alternative that does have compatibility with classic winamp skins
Exaile: another itunes like app, but also does a fair job
XMMS: its not quite dead as everyone says it is, there has been a new release of it just recently so maybe XMMS is on the rebound

---

### Post by awthomp on 2007-12-13
> **djbon2112 said:**
> Just did... it says it's installed, and I installed all the plugins, but there's still no shortcut or anything to launch it!

There's nothing to launch with the plugins... they're not actual executable programs.  If you try to play an mp3 in Rhythm Box now, it should work.

---

### Post by djbon2112 on 2007-12-13
> **awthomp said:**
> There's nothing to launch with the plugins... they're not actual executable programs.  If you try to play an mp3 in Rhythm Box now, it should work.
It's all already been ripped, downloaded, etc. It's a 110 GB mess of files that'll take weeks to organize. No thanks!

As to XMMS2, I know you can't launch the plugins, but isn't XMMS2 a seperate music player? I'm a little confused about that.

---

### Post by awthomp on 2007-12-13
Why don't you try to download something similar to MusicBrainz.  It fixes all of your mp3 tags.  I'm assuming this is why your music isn't organized?

I don't know the best MusicBrainz type program for Ubuntu (I've never used it - only heard about it), so maybe through your own research or from another community memeber you'll get a suggestion.

---

### Post by djbon2112 on 2007-12-13
I don't think you guys understand what I mean by "disorganized"...

I've got 110 GB of music, well taged, but often with non-descriptive filenames, jumbled into one folder basically. With Winamp I could just add that folder to my Media Library and bam it was organized for me. Since none of these players have a media library, my entire collection is hopeless to navigate.

---

### Post by awthomp on 2007-12-13
> **djbon2112 said:**
> I don't think you guys understand what I mean by "disorganized"...

I've got 110 GB of music, well taged, but often with non-descriptive filenames, jumbled into one folder basically. With Winamp I could just add that folder to my Media Library and bam it was organized for me. Since none of these players have a media library, my entire collection is hopeless to navigate.

Amarok does.  It even watches the folder to see if any new music is added!  I'm pretty sure most (if not all) of the major music players have a library function.

---

### Post by screaminj3sus on 2007-12-13
Rhythombox has a pretty good library, I also like Banshee alot. Rhytmbox will watch your folder for new music and add it aswell.

---

### Post by djbon2112 on 2007-12-13
> **awthomp said:**
> Amarok does.  It even watches the folder to see if any new music is added!  I'm pretty sure most (if not all) of the major music players have a library function.

Audacious doesn't (yet), and it's the app I like best, so I guess I'll just live without one for awhile, or just go and organize my music. I've got time to kill ;) And I'm personally not a fan of Amarok, or anything organized like iTunes for that matter. Media library and current playlist/queue should be seperate.

Thanks guys!

---

### Post by cluepon on 2007-12-13
Amarok makes WinAmp look like a speak-n-spell. it's one of the finest pieces of open source software ever produced. Just about every feature you could ever want, album art, lyric fetching, last.fm integration, live directory scanning, SQL backend, the list goes on and on. Amarok balances eye candy with functionality pretty well. It's not one over the other, for the most part. The result is a commercial grade software package which is free.

---

### Post by awthomp on 2007-12-13
I agree with cluepon.  Amarok is one of the main reason why I started using Linux full-time.

---

### Post by hhhhhx on 2007-12-14
xmms??

---

### Post by disturbedite on 2007-12-14
> **djbon2112 said:**
> As for Audacious, as far as I can tell, it doesn't have a media library feature, which as I said is the main thing for me right now.
i see.  there is a niche for everyone.  i don't want or need a media library, so audacious is perfect for me.  if i did, i'd use amarok, which i do have installed, but i don't really use it any more.

> **xhhux said:**
> xmms??
read [my post above]("http://ubuntuforums.org/showpost.php?p=3945995&postcount=18") please.

---

