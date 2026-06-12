---
title: "Rhythmbox keeps deciding I can't use it"
date: 2011-05-06
forum: Multimedia Software
---

### Post by ruquay on 2011-05-06
I like Rhythmbox more than any other music player for the simple reason that it has "Genre, Artist, Album" browsing available and doesn't shove the concept of playlists in my face, when I don't care about playlists 99% of the time.  So I want to keep using it.

But lately (some months ago) after trying an upgrade to 10.10, and switching back to 10.04 (unsolvable network issues), Rhythmbox has recognized that its database has been touched by a newer version, and refuses to start.

So I took the next natural step: ~$ find . -name '*rhythmbox*'.  Which led me to find ~/.gconf/apps/rhythmbox, which I promptly moved to ~/.gconf/apps/rhythmbox.bak.  Lo and behold, Rhythmbox decided to start on the next try.  But then, after a new start, something mysterious (to me) happens, and Rhythmbox decides it can't start again.  So now I'm up to something like ~/.gconf/rhythmbox.bak12 (my philosophy: why throw away any data when you are still at 10% drive usage?), and I'm hoping that there is a guru out there who can say something along the lines of, "oh yeah, just delete ~/.secretstuff/rhythmbox-please-behave-badly, and that'll take care of it".

Am I in luck?

---

### Post by Yellow Pasque on 2011-05-06
Start it from the terminal to see why it won't start.

---

### Post by ruquay on 2011-05-08
Sorry, I should have been more clear.  What I mean is that I get the same dialog the next time I start, which is:

[INDENT]The database was created by a later version of Rhythmbox.  This version of Rhythmbox cannot read the database.
[/INDENT]

So I suppose that moving the ~/.gconf/apps/rhythmbox doesn't actually fix the problem, but it seems to temporarily... which confuses me.

---

