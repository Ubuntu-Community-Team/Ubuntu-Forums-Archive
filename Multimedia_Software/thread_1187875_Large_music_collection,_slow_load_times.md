---
title: "Large music collection, slow load times"
date: 2009-06-15
forum: Multimedia Software
---

### Post by Bealer on 2009-06-15
Hi

I've got a large collection of music, over 25,000 tracks. I've been playing around with various media players trying to find the best one to work with my collection. I've tried:

Rhythmbox - it initially loads quickly, but upon loading up does a sort of scan/check for a while. If I do anything while it's doing that it sometimes freezes up. The main thing I don't like about Rhythmbox is that it looks a little old, and lacks features of the other players.

Banshee - a nice media player, but the intial load is awful. Takes around 20 seconds. It half loads up, then goes "grey" and takes a while to load up. I like its features although it's missing the "watch my music directory" auto add feature I like.

Songbird - I like this the most, it's a bit more than a music player. The songkick and last.fm stuff in it is very handy. It however isn't in the repo's, and it takes 20 seconds or so too, to load up. In fact I click to open it, and I wouldn't know anything is happening, then after 20 seconds it appears.

Was just wondering if there are any other suggestions I could try (not Amarok I don't like it). 

And also, are there any ways to get it to load fast?
Could I somehow register it on boot, so it opens faster?

---

### Post by Gen2ly on 2009-06-15
wow, that is alot!  I know you don't like Amarok but it might be your only go.  Amarok uses the mysql database which is very good for very large tables.

---

### Post by Bealer on 2009-06-15
Yeah :) years and years worth of collecting. About 10 actually.

Hmm yeah I thought similar, although Songbird runs using SqlLite too. In fact I think Banshee does too unless I'm mistaken.

I've installed "preload", gonna see if I can get it to silently initialise my music player in the background upon bootup. So when I do come to open it, it opens up in a flash.

Also all the above players. Once loaded they're generally ok. And if I close > open them. They open up pretty quick (are in memory at this point I would guess).

---

### Post by dartmusic on 2009-06-16
I have a collection of over 50k tracks and the only player that I can use reliably is Amarok 1.4.  It literally opens in less than 5 seconds and is ready to play about 5 seconds after that.  I am running Ubuntu Jaunty and would prefer something gnome based, but for all the perks (flawless iPod and USB mass storage syncing, with transcoding, last.fm based dynamic playlists, artwork handling, and general system speed) I've found nothing (outside of Listen) that works as well.  Listen will be a great program in a couple of releases, but there's a nagging problem where it randomly stops after tracks with no rhyme or reason.  You simply have to skip to the next track, but it's nonetheless annoying.  Until then, I recommend using Amarok until it's no longer usable, or someone picks up the project.

---

