---
title: "Rubyripper Incorrectly Files Various Artists"
date: 2009-07-19
forum: Multimedia Software
---

### Post by londonali1010 on 2009-07-19
I'm wondering if anyone else has had trouble with their "various artists" filenaming schemes in Rubyripper?

I prefer to file my various artists track under the artist, then album, just as if they weren't part of a compilation, then I use my music player to group the album together if I want to listen to it.  However, when I put %va/%b/%t in the filenaming schemes in Rubyripper, it just writes them all to the same folder as though the artist were "%va"!

Any suggestions?  I've got loads of compilations/soundtracks and I don't want to have to fix them all manually!

---

### Post by hugmenot on 2009-07-23
Don&#8217;t know much about rubyripper. But you could fix it after the fact automatically with another tool, if you don&#8217;t mind. 

I would suggest Ex Falso for that (package exfalso). You can recursively select your whole Music folder and let it shuffle around the whole batch according to your wishes (in the Rename Files tab). It won&#8217;t delete the then empty folders afterwards however.

---

### Post by londonali1010 on 2009-07-23
> **hugmenot said:**
> Don’t know much about rubyripper. But you could fix it after the fact automatically with another tool, if you don’t mind. 

I would suggest Ex Falso for that (package exfalso). You can recursively select your whole Music folder and let it shuffle around the whole batch according to your wishes (in the Rename Files tab). It won’t delete the then empty folders afterwards however.

Thanks. I have actually done that before, using Amarok, which can rename all your files according to their tags. But I don't like using Amarok to play music, so I don't keep it on my system. However, I'm going to have to if the bug doesn't get fixed soon!

Incidentally, I have filed a bug report for this issue, which is now accepted, on the Rubyripper Google code site, so hopefully it will get fixed soon! :)

---

### Post by hugmenot on 2009-07-24
Now that I look at your string, why do you use %va anyway? If you want everything to be sorted by artist first, then why don&#8217;t you place a %a in the front? It seems to be doing what you requested, i.e., it sorts VA under VA because you use %va?

But that&#8217;s all guesswork. Maybe I should shut up now.

---

### Post by londonali1010 on 2009-07-27
No, don't worry..I did try that. The problem is, if you mark something as "various artists", the ARTIST field is "Various Artists" and the VARIOUS ARTIST field is the track artist. (Because you can only have one artist per album.) So if I just use %a instead of %va, it files everything under Various Artists/<album name>/<track name>, which is the same thing that happens if you don't mark it as "various artists" in the track listing tab.

Evidently, it is just a problem in the filenaming part of the Rubyripper code, probably missed when some other code changed.

---

### Post by hugmenot on 2009-07-27
Well, that&#8217;s a strange system anyhow. What I&#8217;m used to is the artist vs. albumartist [distinction]("http://www.mkoby.com/2007/02/18/artist-versus-album-artist/").

In effect, you tag each track with the proper artist that performed the track and for the whole thing you use album artist so you can group the album into whatever you please, even if it&#8217;s simply &#8220;Various Artists&#8221;.

The disadvantage is that many simple players don&#8217;t give a damn about album artist and ingore it. But on the other hand some players do. Among them notably iTunes and Windows Media.

Myself I mostly have classical music, which is a bitch to tag when you want to retain a minimum of compatibility with simple players but still have rich tags. So I resorted to always use the composer for &#8249;artist&#8250; but I at least add &#8249;performer&#8250; and &#8249;conductor&#8250; as well. And If the CD has pieces from several composers I add &#8249;albumartist&#8250; and fill it with something that seems to make sense (mostly one of either conductor or performer, depending of which one is more succinct).

I won&#8217;t mention that I often even add things like &#8249;instrumentation&#8250;, &#8249;part&#8250;, and &#8249;opus&#8250; lest you think I&#8217;m mad. But I&#8217;m constantly irritated that in Linux Quod Libet is the only player that supports this free scheme.

---

