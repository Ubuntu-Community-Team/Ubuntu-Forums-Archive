---
title: "Music library organisation in Banshee"
date: 2011-06-13
forum: Multimedia Software
---

### Post by dsfitzpat on 2011-06-13
Now that Ubuntu has moved to Banshee as the default music player, I'm curious about the following: what solutions have users with large music libraries found for keeping things organised in Banshee?
As far as I can tell, there is only one way to sort music in Banshee - first by artist, and then by album.  I've got a fairly large music collection, which spans everything from folk to rock to classical, so I like to be able to sort first by genre.  (For example, if I feel like putting on some jazz, it's nice to not have to scroll through piles of classical and folk to pick out the handful of jazz albums I have.)
As far as I can tell, there's no way to do this in Banshee.  Are there any workarounds?  What about being able to sort classical according to either composer or performer?
If anyone has found solutions with Banshee, I'd like to hear them, since Banshee seems to have a lot of fans.  (Of course, I've heard on other threads that using a music player to play locally stored music makes me hopelessly behind the times, so maybe I am just not the target market for Banshee!)

---

### Post by veryaner on 2011-08-06
Did you find a soulution? I have a similar problem, my music collection is organized as Artist/(year) Album/* and I want to keep it like that!

---

### Post by dsfitzpat on 2011-08-06
My solution was to switch to Clementine.  It's in QT so it looks a bit out of place, but it's based on Amarok 1.4, which I still think was better than anything that's come since.  (Some of these comments might apply to Exaile as well, although I don't have it installed at the moment - it has HAL as a dependency.)
It uses a tree view, which I like, and there is an 'advanced grouping' feature, where you can pick your favourite three categories (including year) for sorting.

I'm also still using Rhythmbox since it supports the grouping I use (but is not as customizable) and it works with my mp3 player (an old Sansa).  Clementine is supposed to support MTP devices but doesn't seem to work with mine for some reason. (Device support in Amarok 1.4 was fantastic - I don't know what's stopped everyone from implementing something similar in another program.)

---

### Post by Clive McCarthy on 2011-08-15
> **dsfitzpat said:**
> It uses a tree view, which I like, and there is an 'advanced grouping' feature, where you can pick your favourite three categories (including year) for sorting.


I have the same issue with Banshee and other music players. They are all geared exclusively to popular music with a  hierarchy of performer/album/song. It's disappointing that there is no automatic hierarchy for classical music organized by composer/album/performer/multi-track work.

I've tried Rhythmbox, Banshee, Listen, Clementine but I have to say that they are all about the same. It does seem a sad waste of programming effort to have so many choices that are largely (to me) indistinguishable where NONE of them offer decent classical music support. 

I have not been able to find the 'advanced grouping' facility in Clementine.

I have just fired up Exaile with much the same impression. It seems that the meta-data associated with my MP3 files correctly identifies the 'classical' genre correctly. It seems that the 'collection' listing of all the players ALWAYS sorts by performer. It would make so much sense to have it sort conditionally based on genre. [COLOR="Blue"]**If genre == rock then sort by performer, if genre == classical sort by composer**[/COLOR]. How hard is that?

I found the 'advanced grouping' facility (hidden under **wrench>group_by>advanced_grouping**) so Clementine might be the way...

---

### Post by dsfitzpat on 2011-08-15
I was about to reply with directions to the advanced grouping, but your edit beat me to it!  Well, in case anyone else comes across this thread, I've attached a screenshot:
[ATTACH]200092[/ATTACH]

---

### Post by Clive McCarthy on 2011-08-15
I have just installed Clementine on one of my desktop machines which allows me to explore things more comfortably. The 'target' machine which is running Clementine is hooked up to my main sound system which is stashed in a closet. I realize that the UI of Clementine (and other players) is aimed at principally desktop use.

I'm going to use Ubuntu's remote desktop to control the thing...

---

