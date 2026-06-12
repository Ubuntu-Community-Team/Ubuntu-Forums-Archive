---
title: "A good audio player?"
date: 2007-01-28
forum: Multimedia &amp; Video
---

### Post by other on 2007-01-28
I can't seem to find a good audio player. I've tried Amarok, Rhythmbox, Banshee, Listen, Muine, GMPC (with mpd), Quod Libet, and some other mpd clients. Maybe I didn't give them the time that they deserve, so speak up if you think that I've missed something. I probably gave Amarok the most time, and I can't understand why people like it. I couldn't control anything. Is there something that I'm missing? It just seemed to force its way on me.

What is absolutely neccessary is that the audio player has support for gapless playback and global hotkeys. There are a lot more things I want, but if I start out with these requirements, what audio players are there?

---

### Post by thelocust on 2007-01-28
[B]
I dont do alot of audio but check out [COLOR=Blue][songbird]("http://www.songbirdnest.com/")[/COLOR]. Its still in development but it looks pretty already and it has extentions like firefox so the possibilities are endless. [/B]8)

---

### Post by TheWizzard on 2007-01-28
euh, what's your problem with amarok? it's the best i've ever seen and you're in total control.

---

### Post by Uncle Spellbinder on 2007-01-28
> **other said:**
> I probably gave Amarok the most time, and I can't understand why people like it. I couldn't control anything. Is there something that I'm missing? It just seemed to force its way on me.
I believe you are indeed missing something. I couldn't live without it. Better than iTunes or Winamp, in my opinion.


> **other said:**
> What is absolutely neccessary is that the audio player has support for gapless playback and global hotkeys. There are a lot more things I want, but if I start out with these requirements, what audio players are there?
Gapless playback? Not sure if Amarok supports it yet (or anyone else other than iTunes for that matter). Aside from that, nothing beats Amarok.

---

### Post by RomeReactor on 2007-01-28
I haven't used [XMMS]("http://www.xmms.org/") in ages, but since you didn't mention it maybe you haven't tried it yet. Also check out its [Wikipedia]("http://en.wikipedia.org/wiki/XMMS") entry. It doesn't blend in with gnome unless you skin it, though. [BMP]("http://bmp.beep-media-player.org/index.php/BMP_Homepage") is similar, though it was heavier and slower to respond (but as i said, haven't tried either in a long while). It looks better than XMMS on gnome, though. Anyway, here's its [Wikipedia]("http://en.wikipedia.org/wiki/Beep_Media_Player") entry; give either a spin, they're in Synaptic/Adept, or:

```
sudo apt-get install xmms
```

```
sudo apt-get install beep-media-player
```

---

### Post by Tanker Bob on 2007-01-28
My problem with Amorok is that is crashes unceremoniously every time I try to play a RealPlayer file.  The codecs are installed both in RealPlayer and xine engines and properly cited in xine's configuration file, but Amarok cannot seem to handle the files.  It also will not catalog RealPlayer files, not crashing but providing an error box.  Kaffine, xine, and gxine have no problems with Real format.

Best I can see, Amorok is still a work in progress.  Until they sort all this out, I use Kaffine for most things and VLC for flv files.  RealPlayer 10 still does the best job with its own files.

---

### Post by other on 2007-01-29
> **Uncle Spellbinder said:**
> I believe you are indeed missing something. I couldn't live without it. Better than iTunes or Winamp, in my opinion.

But both iTunes and Winamp are horrible players. :)

> Gapless playback? Not sure if Amarok supports it yet (or anyone else other than iTunes for that matter).

It's not like iTunes was early with gapless playback, it took them forever to add it. I thought it was standard in most other players, but apparently not?

When I get back from school I can write down what it is that I don't like about Amarok. Of course, it's a big problem if it doesn't support gapless playback. But what also annoyed me a lot was that it didn't allow me to sort my music how I want. I think I might've been spoiled by foobar2000, too bad it only runs on Windows. :/

> **RomeReactor said:**
> I haven't used [XMMS]("http://www.xmms.org/") in ages, but since you didn't mention it maybe you haven't tried it yet. Also check out its [Wikipedia]("http://en.wikipedia.org/wiki/XMMS") entry. It doesn't blend in with gnome unless you skin it, though. [BMP]("http://bmp.beep-media-player.org/index.php/BMP_Homepage") is similar, though it was heavier and slower to respond (but as i said, haven't tried either in a long while). It looks better than XMMS on gnome, though. Anyway, here's its [Wikipedia]("http://en.wikipedia.org/wiki/Beep_Media_Player") entry; give either a spin, they're in Synaptic/Adept, or:

I'm sorry, I have already tried it. I really appreciate the tip though. :)

---

### Post by deadlydeathcone on 2007-01-29
> **other said:**
> It's not like iTunes was early with gapless playback, it took them forever to add it. I thought it was standard in most other players, but apparently not?

I believe that mpd is the only player for Linux that fully supports it. Amarok is supposed to come pretty close, but I haven't payed attention to that player in a while so I'm not sure how well it pulls it off.

Anyways you should look into a good mpd frontend; there's about a billion of them and one of them should work for you. As far as graphical versions go the svn of GMPC is my favorite by far (I'm not sure if you tried that or the one in the repo; they're very different), with maybe Sonata in second. I'm pretty sure you'll like the svn, as it has a really nice tag browser that lets you sort through your library in a huge number of ways, some nice plugins and even manages to look good.

You can find lists of other clients [here]("http://en.wikipedia.org/wiki/Music_Player_Daemon") and [here]("http://mpd.wikia.com/wiki/Clients") if you want to take a look.

---

### Post by other on 2007-01-29
> **deadlydeathcone said:**
> Anyways you should look into a good mpd frontend; there's about a billion of them and one of them should work for you. As far as graphical versions go the svn of GMPC is my favorite by far (I'm not sure if you tried that or the one in the repo; they're very different), with maybe Sonata in second. I'm pretty sure you'll like the svn, as it has a really nice tag browser that lets you sort through your library in a huge number of ways, some nice plugins and even manages to look good.

I have only tried the one in the repositories, so I'm going to check out the svn. But, is there any way to get support for global hotkeys, either with GMPC or some other mpd client?

---

### Post by deadlydeathcone on 2007-01-29
> **other said:**
> I have only tried the one in the repositories, so I'm going to check out the svn. But, is there any way to get support for global hotkeys, either with GMPC or some other mpd client?

Yes, I took a [screenshot]("http://www.ubuntuforums.org/attachment.php?attachmentid=24115&stc=1&d=1170070363") that shows the config for hotkeys ui (and the tag browser as well). Of course you could always just bind commands for the console mpd client and go that route.

It really is a nice player, and I made some packages for the svn version that you can find in my signature. Hope it works out.

---

### Post by other on 2007-01-29
> **deadlydeathcone said:**
> Yes, I took a [screenshot]("http://www.ubuntuforums.org/attachment.php?attachmentid=24115&stc=1&d=1170070363") that shows the config for hotkeys ui (and the tag browser as well). Of course you could always just bind commands for the console mpd client and go that route.

It really is a nice player, and I made some packages for the svn version that you can find in my signature. Hope it works out.

That seems great! I'll try it tomorrow, because tonight I have to study, unfortunately. :) I'll report back.

---

### Post by glabouni on 2007-01-29
> **other said:**
> I can't seem to find a good audio player. (...) I probably gave Amarok the most time, and I can't understand why people like it.  (...)


+1

> **other said:**
> But both iTunes and Winamp are horrible players. :)
 I think I might've been spoiled by foobar2000, too bad it only runs on Windows. :/


+1

I don't get what everybody seem to find so great about amarok. 
first thing first, it simply fails to manage my ogg files with a "too many errors" reason without giving any clues about how to fix this, but that doesn't prevent amarok from trying again each time I open it, and failing miserably each and every time. Apart from this personal problem, I find it hard to find anything in it. 

I'm curently giving songbird a try, although it is great for online music browsing and listening, it's a poor audio player in terms of usability (still a work in progress), it doesn't seem like it's going to replace a local audio player.

I have yet to find a simple and easy to use audio player for linux, and I sure miss foobar2000.

---

### Post by shrimphead on 2007-01-29
Exaile is a great player.  It's based on amarok but don't let that put you off, it's still in development so it hasn't managed to accumulate the bloat yet :P

---

### Post by glabouni on 2007-01-29
just to add official website link for [exaile]("http://www.exaile.org")

---

### Post by zibi on 2007-01-29
I'm having the same problem: i just want a light audio player with no library manager and stuff like this. 
The best for me would be something like VLC. I would prefer not to use it since in some cases it behaves  unfairly (if you select and open more files simultaneously, it opens different windows and play all songs together :guitar: ).
The simpler player I've found is MUINE but it doesn't play CDs...

---

### Post by Torajima on 2007-01-29
> **other said:**
> But both iTunes and Winamp are horrible players. :)



It's not like iTunes was early with gapless playback, it took them forever to add it. I thought it was standard in most other players, but apparently not?


iTunes has always had gapless playback... what took Apple forever was to add it to the iPod...

I actually like iTunes (except there is no easy way to backup your playlists); is there a Linux audio player that has smart playlists and shows album art?

---

### Post by Torajima on 2007-01-29
Actually Songbird looks pretty darn cool... I'll have to try that!

---

### Post by Protoss on 2007-01-29
> **Torajima said:**
> iTunes has always had gapless playback... what took Apple forever was to add it to the iPod...

I actually like iTunes (except there is no easy way to backup your playlists); is there a Linux audio player that has smart playlists and shows album art?

Exaile has album art support, along with Smart Playlists. Its even got iPod support.

---

### Post by other on 2007-01-30
> **Torajima said:**
> iTunes has always had gapless playback... what took Apple forever was to add it to the iPod...

No, iTunes didn't have gapless playback until version 7. All it had before that was "crossfading", which is not the same in any way.

---

### Post by other on 2007-01-30
I have now tried the svn version of GMPC, and it seems to be the best player I've tried for GNU/Linux. It's definitely lacking a lot, some of it seems to be due to limitations in mpd, but it's still better than the other alternatives. I have not yet tried Exaile, but I will once I can justify spending some time on it. ;)

Thank you all for your suggestions and comments.

---

### Post by elpresidente on 2007-01-30
> **other said:**
> I have now tried the svn version of GMPC, and it seems to be the best player I've tried for GNU/Linux. It's definitely lacking a lot, some of it seems to be due to limitations in mpd, but it's still better than the other alternatives. I have not yet tried Exaile, but I will once I can justify spending some time on it. ;)

Thank you all for your suggestions and comments.

I highly, highly, recommend Exaile!

---

### Post by deadlydeathcone on 2007-02-01
> **other said:**
> I have now tried the svn version of GMPC, and it seems to be the best player I've tried for GNU/Linux. It's definitely lacking a lot, some of it seems to be due to limitations in mpd, but it's still better than the other alternatives. I have not yet tried Exaile, but I will once I can justify spending some time on it. ;)

Glad you liked it. If you find a better foobar-like let us know, I'll be all over it.

I updated the packages that I linked to, and will probably update them until gmpc v14 gets released. It just started getting worked on again about a month after the developers hard drive crashed, so hopefully there's some good things coming soon.

---

### Post by qball on 2007-02-02
> **deadlydeathcone said:**
> Glad you liked it. If you find a better foobar-like let us know, I'll be all over it.

I updated the packages that I linked to, and will probably update them until gmpc v14 gets released. It just started getting worked on again about a month after the developers hard drive crashed, so hopefully there's some good things coming soon.

I hope to make a release of gmpc soon. I now concentrate on fixing bugs bugs. Hope todo a RC1 release this weekend.. 

One of the delays is my busy schedule, the other is that I am waiting for some modifications that are needed to support Avahi (mpd supports avahi in svn).  But I intend to make a RC1 this weekend if it's not in then, to bad..

I intend (again) to make more smaller releases after that..

---

### Post by glabouni on 2007-02-03
I'm now using foobar2000 with wine. 

AFAICT it works as intended for the listening part. I have yet to try the other features.

---

### Post by bhathco on 2007-02-03
Bleep is simple and sweet.

---

### Post by bhathco on 2007-02-03
I mean Beep!

---

### Post by bom28 on 2007-02-03
It doesn't support gapless playback (as far as I know) but GMusicbrowser is a very interesting alternative. While it has some rough edges, it has a lot of very original features and is very customizable.

---

