---
title: "iPod and cover art"
date: 2008-12-10
forum: Multimedia Software
---

### Post by hollinch on 2008-12-10
Hello all,

I am trying to get at least one music application to sync the cover art on the iPods of my children, but it consistently fails. My son has a 4th generation Nano, and my daughter a 5th generation. I have used iTunes initially to put some music on my son's iPod, together with cover art, but for my daughter's iPod I was forced to download the latest version of iTunes, which prompts some questions I am not prepared to answer. Yet activation of that last iPod at the iTunes store can only happen if I answer these. 

So the only solution would be to put iTunes aside completely, and only use one of the Linux solutions to manage my music collection and to sync the iPods. However, none of the apps I tried syncs the album artwork. Even worse, the existing artwork on my son's iPod disapppeared! Syncing music files works fine, though. Have tried Rhythmbox, Amarok, gtkpod, Banshee and Exaile.

I am really frustrated that this is not working. I have searched through the forums and apparently I am not alone in this, but no one seems to have _the_ solution that works. 

Does anyone have any tips on what to do?

Many Thanks!

---

### Post by Existentialist on 2008-12-15
You should be able to embed the album art with the tagging information using a program like [[COLOR="Blue"]_Easy TAG_[/COLOR]]("http://easytag.sourceforge.net/") or [[COLOR="Blue"]_Picard_[/COLOR]]("http://musicbrainz.org/doc/PicardTagger") with the proper plugin.  I have never used embedded album art on an ipod, so I can't promise the ipod will recognize the art in the tags.  It's a pretty easy thing to try out though.

---

### Post by GeorgeMurango on 2008-12-15
Banshee was able to transfer album art to my third generation nano when it had the album art plugin enabled

---

### Post by hollinch on 2008-12-16
Thanks for your replies, much appreciated.

As for embedding the album art, speaking as an end user (and I am supporting end users myself), I don't want to have to do any additional manual operation to be able to have this available, this would be too cumbersome to do for the thousands of songs I have and use. I would love to have such a feature available the way iTunes provides this currently, e.g. download the album art automatically, and sync to iPod together with the songs without any manual intervention.

And as for Banshee, I have tried it, but maybe I have not enabled the 'album art plugin'? I will check again tonight, it might be that that's the trick I need.

Hmmmm, I would've thought this to be a major feature that quite a number of users would be looking for in modern media players that support iPods, and thus would be requested to be built in as a default feature quite soon. Maybe there's not been such a significant demand for it yet. Well, or there's a lack of developer time, of course. Anyway, I am sure it will come in due time; I am patient, and hugely appreciative of the tremendous developer effort put into these products!

Thanks to the developers.

---

### Post by hollinch on 2008-12-17
Hi again,

Have checked last night, and I noticed that the Banshee album art plugin is described as fetching the album art. Additionally, it is enabled by default (I could only disable the plugin). So I assume this plugin doesn't handle the transfer of album art to the iPod. Or maybe it tries but fails, for some unknown reason. Is there a way to find out if that is the case?

I will have a look at Easy TAG and Picard, to know what that solution offers and what is involved to get that working.

Thanks/JH

---

### Post by outphase on 2008-12-20
Banshee was able to get album art onto my 4th Gen iPod Nano. However, subsequent syncs caused the previous album arts to go missing.

---

### Post by Zeedok on 2008-12-20
I also have had some problems with how Banshee handles iPod album art.  I started using Picard a month or so ago (BTW you can fairly quickly retrieve and save album and band information with Picard - and album art after added their album art plugin).  I think that iTunes and Banshee handle might album art differently - for instance when I put a new album on my iPod with Banshee the artwork shows up, but if I replace some music with Banshee (ie that iTunes had already put on with associated artwork) the iTunes artwork prevails!!

I'd be interested if anyone else has worked this out, because we're kind of stuck until the Banshee developers add a album art editing dialogue.

---

### Post by mlmartinet on 2008-12-27
Here is what is happening to me.  I keep a copy of the album art in the folder of the album.  On initial sync every thing works out just fine but then if I go to add more music it erases all the previous art work.  I own the iPod Nano 4th gen.  I was wondering if any one else was seeing this same problem.  I've been googling it like crazy and haven't come up with any solutions.

---

### Post by euchrid33 on 2008-12-29
I've got the 4th gen nano, which I load using Amarok.  I've had no problem with getting the cover images onto Cover Flow - in fact, they went over automatically when I loaded the songs on.  They're only on Cover Flow, though, not in the standard browsing menu or on the Now Playing window.

There's been some discussion here:

[http://ubuntuforums.org/showthread.php?p=6445298](http://ubuntuforums.org/showthread.php?p=6445298)

It seems like libgpod is the core of the issue, though how it should be altered to ensure that the iPod behaves properly is still anyone's guess.

---

### Post by Master Chief on 2008-12-30
> **hollinch said:**
> ...I have used iTunes initially to put some music on my son's iPod, together with cover art, but for my daughter's iPod I was forced to download the latest version of iTunes, which prompts some questions I am not prepared to answer...

Eh, I don't understand this.  I mean; what questions did you need to answer?  I even downloaded iTunes two minutes ago, but I wasn't asked to answer any questions!

---

### Post by levelup3 on 2008-12-30
Thanks for all your post

---

### Post by hellz99 on 2008-12-30
Amarok can move the cover art.  Just make sure you have the correct ipod model set.

---

