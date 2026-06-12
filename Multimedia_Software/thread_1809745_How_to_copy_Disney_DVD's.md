---
title: "How to copy Disney DVD's"
date: 2011-07-22
forum: Multimedia Software
---

### Post by hinge on 2011-07-22
OK, I'm not doing anything illegal. I simply rip all my PURCHASED DVDs to XVID and let my kids watch them through XBMC.

Some DVD are simply unrippable, among them are 

[Open Season]("http://www.imdb.com/title/tt0400717/")
[Wall E]("http://www.imdb.com/title/tt0910970/")
[Bolt]("http://www.imdb.com/title/tt0397892/")
[Up]("http://www.imdb.com/title/tt1049413/")

I cannot play or rip them using mplayer/mencoder. I have been able to rip the UP image to an ISO using ddrescue. But the resulting image seems bad. when I play track 50 the movie is played, but the chapters are sequenced in the wrong order. I have seen similar behavior with Bolt and Wall E.

Are anybody seeing the same behavior?
Is there a solution for this?

:confused:

---

### Post by andrew.46 on 2011-07-22
Unfortunately I do not have any of these dvds so I cannot test these specific ones :(. Hev you tried copying the dvds to your drive using vobcopy? The following command will mirror the dvd to your drives and will also decrypt with libdvdcss if this is present on your system:

```
vobcopy -m
```

Just ensure that this is legal in your part of the world, legal enough here but I believe the US has some problems with personal backups of dvds?

---

### Post by mc4man on 2011-07-22
If you didn't care about doing a whole disk rip (& xvid), then handbrake would likely be able to deal with these structure protected titles as a main movie rip and encode.
It does keep up with some of the Sp tricks and should be able to get the right titleset/title

As far as dumping to an encrypted and structure protected iso as you're doing with ddrescue (I do occasionally but use dvdisaster instead.
If you're having any playback issues than it's probably the player you're using or you if you're specifying the title #, not the protection. 
(I can't 100% say what ddrescue does, never used, but have used dvdisater on some tough Sp titles and the iso is fine with a good player

On such iso's the structure protection is in most cases irrelevant, it's no different than playing back the orig. disk itself.
If the title is playable from the orig. disk then the iso is the same thing.

As far a linux rippers for the _whole disk with menus_, k9copy can handle some Sp titles, overall no linux ripper is in a position to keep up with changes and variations in Sp.

Mplayer is unfortunately not that good at Sp title navigation, vlc or totem-xine are much better, totem-xine being the most reliable with navigating sp titles.

> when I play track 50 ... 
Are you 100% sure that is the correct title #? I could ck. on  a couple of those titles fairly easily but being in a diff. region possibly not too useful.
(I have a post somewhere in this forum about wall-e from a couple of years ago, could be hard to find and maybe not useful, I forget what was in it.

Edit:
I see from old post that in R1 the real main title for wall-e was title 30

---

### Post by mocha on 2011-07-22
Have a look at the Doom9 forums in the Linux and Decrypting sub-forums.  Someone there came up with a method using ddrescue and a small C program to fix the garbled sectors in the resulting iso.  Sorry I don't have a direct link at the moment.  I've successfully used it on many Arrcos protected (or whatever it's called) DVDs from Disney.  Worst case scenario, you can use DVDfab decrypter in Wine.

---

### Post by mc4man on 2011-07-22
> **mocha said:**
>  using ddrescue and a small C program to fix the garbled sectors in the resulting iso.  Sorry I don't have a direct link at the moment.  I've successfully used it on many Arrcos protected (or whatever it's called) DVDs from Disney..

What it does is remove the css protection from an iso without the need to extract. (and does a good job of it, could fail on very small sample extras
That would give you a decrypted but still structure protected iso, though as mentioned the Sp is generally irrelevant for playback from an iso

(probably about 6 - 9 months  back in doom9 archive if looking for

---

### Post by Mcjohnnson on 2011-07-22
DVDFab HD Decrypter with WINE is working on such things, but I do not know if it is legal to use it in your country.

---

### Post by hinge on 2011-07-24
Thanks for the replies.

I think that I figured it out. It was not track 50 but 24 or 25. I have the nordic DVD. It is ripping right now so I haven't seen the final result yet....

---

### Post by Mcjohnnson on 2011-07-24
Did it work?

---

