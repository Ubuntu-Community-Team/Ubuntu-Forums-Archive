---
title: "Quicktime Trailers - Firefox &amp; Gnome MPlayer"
date: 2010-08-25
forum: Multimedia Software
---

### Post by Ajc on 2010-08-25
I've just tried to play a quicktime trailer via FireFox which I've done in the past. GNOME MPlayer kicks in as before, and you can see the trailer cache downloading.
... however even after the cache is 100% nothing happens.

so with Gnome MPlayer, tried to load location ... and same thing happens.

Opened Movie Player to load location of quicktime file, and it plays fine !!

has something changed with GNOME Player, or are Apple playing around again as they have in the past?

Ajc

---

### Post by andrew.46 on 2010-08-25
Hi ajc,

I am at the wrong computer at the moment to test the trailers from firefox but you might be intrigued to know that the next release version of vlc should support playback of these trailers from within the playlist:

[http://ubuntuforums.org/showpost.php?p=9750531&postcount=143](http://ubuntuforums.org/showpost.php?p=9750531&postcount=143)

and certainly this was working well enough 2 days ago...

Andrew

---

### Post by lovinglinux on 2010-08-26
Not working here either.

---

### Post by mc4man on 2010-08-26
Probably something that needs to be adjusted in either the plugin or gnome-mplayer(don't have neither atm on maverick

Generally prefer the totem-mozilla plugin in most cases anyway - for apple it works quite well atm
(or opening from the browser in totem
Plus the t-m plugin caches apple trailers relatively quickly, if for whatever reason playback isn''t smooth then I just pause and open the caching file in any player from /tmp

mplayer itself can certainly handle the site - 2 ex.
```
mplayer -user-agent 'QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)' http://trailers.apple.com/movies/focus_features/theamerican/theamerican-dontmakeanyfriends_h480p.mov

```
or 720 w/ a little caching
```
mplayer -cache 8192 -user-agent 'QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)' http://trailers.apple.com/movies/focus_features/theamerican/theamerican-dontmakeanyfriends_h720p.mov
```

As Andrew mentioned vlc 1.2 is doing the trailers quite well from playlist -> internet

Ot
just used the Foxtester ext. on maverick - working quite well - decided to make 4.0b4 the default
(had a small issue with the ext. being installed once I switched defaults though all is well now

would also love to see browser plugins available thru update-alternatives, that way one could install themall andswitch quickly as desired - don't see that happening though

---

### Post by andrew.46 on 2010-08-26
Hi mc4man,

And of course for offline viewing:

```

wget --user-agent='QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)' \
http://trailers.apple.com/movies/focus_features/theamerican/theamerican-dontmakeanyfriends_h480p.mov

```

Andrew

---

### Post by mc4man on 2010-08-26
Went ahead and installed gnome-mplayer - as a standalone it works fine  from 'location' or cli, so it's 'plugin' feature is fine
```
gnome-mplayer http://trailers.apple.com/movies/focus_features/theamerican/theamerican-dontmakeanyfriends_h480p.mov
```

So the issue lies with the gecko-mediaplayer browser plugin (at least w/ firefox ver. i'm using.

(maybe file a bug against gecko-mediaplayer, I think they're pretty good at trying to keep up.

Screen shows how fast the t-m plugin caches - paused just a cache was complete

---

### Post by andrew.46 on 2010-08-26
vlc 1.2.0 will have a huge feature on its hands with the Apple Trailers built in :). Looks like Maverick will miss out though...

Andrew

---

### Post by mc4man on 2010-08-28
> Looks like Maverick will miss out though...

at best 10.10 may get 1.1.4, whether the appletrailers lua works there don't know - have decided to go w/ 1.2  (upped the http (https) caching a bit from the default of 1200 (1.2 sec) to allow for network variances

While no longer using the daily 1.2 ppa for 10.10, it may prove to be a good deal for many as long as they keep in mind there may be some breakages

 - it's an 'autobuild', so no actual testing would likely be done. (though it may at times

---

### Post by andrew.46 on 2010-08-28
Hi mc4man,

> **mc4man said:**
> at best 10.10 may get 1.1.4, whether the appletrailers lua works there don't know - have decided to go w/ 1.2  (upped the http (https) caching a bit from the default of 1200 (1.2 sec) to allow for network variances

Although [1.1.4]("http://www.videolan.org/vlc/releases/1.1.4.html") does not do that much for Linux I guess. Certainly on both the distros I am building 1.2 on there seems an unusual period of stability and I confess I am using it for everyday use now. Only problem is a total program crash on accessing some parts of the Preferences, have a look at the 'Audio' preferences in 'Simple' view...

Can I ask where you set the http caching option? I have hunted through the Preferences without success :(. Certainly it is needed from my part of the world...

> While no longer using the daily 1.2 ppa for 10.10, it may prove to be a good deal for many as long as they keep in mind there may be some breakages

I am even more wary of PPAs these days after reading the various reports of breakages on these forums. It would be nice to have some sort of 'Rating' system in place for PPAs but who would police this?

Andrew

---

