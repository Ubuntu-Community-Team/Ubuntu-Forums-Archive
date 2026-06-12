---
title: "Any good MPD client around?"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by finferflu on 2007-05-08
Hi all,
ever since I tried the MPD, I fell in love with it, the only problem is that I cannot find any good client. What I am basically looking for is a client that supports automatic cover art fetching (like AmaroK, which stats checking locally, then remotely), equalizer, and streaming music.
I am currently using **Sonata**, which is almost there, but I find it very annoying to have to look for the album cover manually every time, or to insert the URL of the stream I want to play manually (I also need to give it a title!), the equalizer is not there, and that's what I miss the most.
I have also tried **gmpc**, but the version in the repos is old, and the last time I tried to install the latest one, I had to go round the net to find the missing libraries. However it hasn't got an equalizer, thus it's not worth spending time on that. 
I have also tried **pympd**, and there is no equalizer either.
The only decent thing I found was a **script for Amarok** that allowed you to manage the MPD, but I couldn't install it (that was on Sidux), and now I am not using KDE anymore, and have no intention to install such a heavyweight application.

So, is there anything else available out there?

Thanks a lot for your time :)

---

### Post by finferflu on 2007-05-09
Anyone?

---

### Post by archivator on 2007-05-12
I don't think you will find any mpd-based player with a built-in equilazer as that should part of mpd and it isn't. In other words, what you call a player is only a front-end to mpd and does not even have access to the audio played.

On a side note, I'm currently running Sonata and it fetches album art automatically (my setting is Local, then Remote). The only annoying thing about the version in the Ubuntu repos is that bug with the player crashing if you have the lyrics window open and the song changes. That's fixed in the newest version, though.

As for gmpc, it's not hard to install at all, there is a deb package at the Debian repositories: [http://packages.debian.org/stable/sound/gmpc](http://packages.debian.org/stable/sound/gmpc) ;)

---

### Post by finferflu on 2007-05-12
Well, that's an old version, like the one in the Feisty repos...

Anyway, I was looking for something on the lines of the Amarok script... so you can have a classical player (with all the standard features, such as the equalizer) accessing the MPD...

---

### Post by aidanr on 2007-05-12
i haven't found a better mpd client than sonata, there's a deb for the latest version [here]("http://www.getdeb.net/app.php?name=Sonata")

i've found it quite good at fetching album art and haven't noticed any problems with the streaming (i guess it could be more automatic though) and equaliser support would be nice (you should post to the mailing list and ask scott his opinion about it) there's already a request on the [mpd tracker]("http://www.musicpd.org/mantis/view.php?id=489")

---

### Post by finferflu on 2007-05-12
Yes, as I have pointed out in the first post, I am currently using Sonata, since it seems the most decent one, but still it could be better... I'll see what I can do with the mailing list, thanks.

---

### Post by archivator on 2007-05-13
I hope you all remember what they say about messengers, bad news, and not killing people.. ;) 

This is an excerpt from the MPDWiki FAQ: 
> Is there an equalizer for MPD?

No, there's no equalizer for MPD, nor are there plans for such a beast. Any kind of software that fiddles with frequencies like this can also be concidered distortion, and it is concidered a much better thing to do this in hardware. Cheap amplifiers/equalizers can be found at a pawn shop for about $20 bucks. Alternatively, you may be able to find a jack output plug-in to do what you want. 

---

### Post by finferflu on 2007-05-13
> **archivator said:**
> I hope you all remember what they say about messengers, bad news, and not killing people.. ;) 

This is an excerpt from the MPDWiki FAQ:
LOL :D

I won't kill ya ahahha! The jack thing could be an intresting option... but at this point I'm thinking about AmaroK... Anyway there *must* be some MPD client not directly related to MPD.. I want to modify the MPD output, so it all should happen on the client side, right? I'm not asking for an equalizer implemented in the MPD itself...

---

### Post by finferflu on 2007-05-14
I have just installed gmpc 0.14 from source, and I have to admit that so far it's the one that looks more promising in terms of features.. of course the look and feel could be improved a bit...

---

### Post by deadlydeathcone on 2007-05-14
> **finferflu said:**
> I have just installed gmpc 0.14 from source, and I have to admit that so far it's the one that looks more promising in terms of features.. of course the look and feel could be improved a bit...

I created proper packages for gmpc+ plugins that work on both Edgy and Feisty, but they're hard to find without searching the forums. When Gmpc 0.15 is released I'm going to contribute my builds to getdeb.net, but until then just check out the link in my sig for debby goodness.

---

### Post by finferflu on 2007-05-15
> **deadlydeathcone said:**
> I created proper packages for gmpc+ plugins that work on both Edgy and Feisty, but they're hard to find without searching the forums. When Gmpc 0.15 is released I'm going to contribute my builds to getdeb.net, but until then just check out the link in my sig for debby goodness.
Where were you when I needed you!?!? :D just kidding :)

Thanks for your contribution, I'll be looking around for you in the future :)

---

