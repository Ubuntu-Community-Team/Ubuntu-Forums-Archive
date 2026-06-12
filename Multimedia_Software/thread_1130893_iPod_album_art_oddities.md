---
title: "iPod album art oddities"
date: 2009-04-20
forum: Multimedia Software
---

### Post by glibdud on 2009-04-20
Hey folks. I recently acquired a 4th gen iPod Nano, and am trying to get it going in Ubuntu 8.10. Rhythmbox recognized the Nano just fine, but didn't seem to want to add music to it. I upgraded libgpod to v0.7, and now it seems to be happy to add music. Unfortunately, when I play the music on the iPod, or try to browse using CoverFlow, the album art doesn't show up.

I browsed these forums and found a few past threads with similar complaints, but here's a twist... one of the albums I transferred to test was Pink Floyd's Dark Side of the Moon. One time while I was at the iPod's main menu, with what's apparently supposed to be the album art scrolling across the bottom, I thought I saw the Dark Side album cover going by as I clicked to move into another menu. I couldn't reproduce it, though, so I thought maybe I was making it up. But then I was playing the Vortex game, and for grins I went to the Now Playing screen within the game... and lo and behold, there's the Dark Side cover. The problem? It wasn't even a Pink Floyd song playing.

So... I guess something's got the cover art all horked up in the database. I'm pretty unfamiliar with how all that is handled internally... is there any way to get a more raw look at what's going on in there? Or, at the very least, could someone help me track down exactly which piece of software (Rhythmbox, libgpod, etc) is causing the problem, so I know where to open a bug report?

---

### Post by Bearded-flower on 2009-04-20
Umm im not shure if this s any help but maybe you should give Banshee a whirl.

---

### Post by Bearded-flower on 2009-04-20
Bump

---

### Post by Simian Man on 2009-04-20
Banshee (IpodSharp) doesn't work as well as Rhythmbox (lbgpod).  Try double-clicking all of your music on the iPod under Rhythmbox.  Sometimes it needs that to transfer the covers.

---

### Post by kpkeerthi on 2009-04-20
I tried many iPod managers. Finally settled with floola. Handles Album art too.

[http://www.floola.com/modules/wiwimod/](http://www.floola.com/modules/wiwimod/)

---

### Post by glibdud on 2009-04-20
> **Simian Man said:**
> Banshee (IpodSharp) doesn't work as well as Rhythmbox (lbgpod).  Try double-clicking all of your music on the iPod under Rhythmbox.  Sometimes it needs that to transfer the covers.

Thanks for the suggestion. Unfortunately, that doesn't work for me. (Which I'm kind of thankful about... I wasn't looking forward to double-clicking 1800 songs).

I may have to check out Floola. I've heard of it, but also heard it's sometimes unstable. Worth a look, I guess.

---

### Post by glibdud on 2009-04-21
...and now last night, I randomly saw the cover to Genesis' Duke show up. So the art is there somewhere, it's just not in the right place.

I'm going to try to find a Windows installation to install iTunes on and see if there are any firmware updates or anything for this Nano. Will report back.

---

### Post by sanjit on 2009-04-21
Using an upgraded iTunes on a friend's laptop to restore my iPod made it more difficult for Linux programs to work with it. My album art isn't showin' up, for instance. I think Apple changed the iTunes database format or somethin'. Now, I have to find someone who HASN'T upgraded iTunes recently.

---

### Post by glibdud on 2009-04-22
> **sanjit said:**
> Using an upgraded iTunes on a friend's laptop to restore my iPod made it more difficult for Linux programs to work with it. My album art isn't showin' up, for instance. I think Apple changed the iTunes database format or somethin'. Now, I have to find someone who HASN'T upgraded iTunes recently.
Heh... well I just upgraded mine (was one minor version behind) and did a restore from a Windows box. It didn't help me at all... same issue. So maybe that's it... newer versions aren't working quite right.

Incidentally, I also tried Floola. It doesn't like the iPod after writing songs to it from Rhythmbox. After doing another restore from iTunes, it complained that it couldn't recognize the iTunes version, but at least it ran. So far I haven't found out how to deal with album art in it, short of possibly embedding it into the tags of each song, which seems horribly wasteful.

So I guess I'm sort of stuck. If it's supposed to work seamlessly in Rhythmbox, then maybe I'll join you in the search for an un-updated iTunes. I take it there's probably no way to "downgrade" it?

---

