---
title: "Scanning media in Banshee w/ Mirage"
date: 2010-01-12
forum: Multimedia Software
---

### Post by granny6989 on 2010-01-12
Has anyone been trying or playing with Banshee and the Mirage plug-in? I set it up to do a media scan, and I'm looking at somewhere in the neighborhood of 18hrs now and it's still going.... More importantly, when this is complete, and I add some new music, will the scan just hit the new tracks, or will it go through the whole library again? If you have any experience with this please fill me in if you can.

Thanks in advance.
S*

:popcorn:

---

### Post by LuisGMarine on 2010-01-12
The best thing to try is opening up banshee through the terminal.  Then try to create a playlist with Mirage and try to catch any funky outputs and hope that you might be catching a bug of some sort.

I've had problems with banshee's mirage plugin, so I stopped using it.  I just tried it again right now and it seems to work ...

---

### Post by granny6989 on 2010-01-13
Actually is ok. I'm using 1.5.2 (Beta), and when it first opens and you set up which folder to watch, it started cataloging music and setting up Mirage simultaneously. I finally killed the Mirage search, and closed and re-opened. Then started the Mirage scan for the second time. I am checking as to whether it is some random bug...

As for time, it took about 3-4 sec a song, and at 11,000 tracks, well, you do the math...

---

### Post by mlissner on 2010-01-13
Yeah, it takes an extraordinary amount of time if you have that much music. It does work well though in my experience. 

As for adding new music, if you read the guy's thesis, you'll learn that it can handle that. If you import a song into Banshee, you'll notice that Mirage is now triggered simultaneously (as it should be). 

Also, you can start using it immediately after it has indexed a song. You don't have to wait until it's done everything. It just won't know about songs that it hasn't yet indexed, but otherwise it will work.

---

