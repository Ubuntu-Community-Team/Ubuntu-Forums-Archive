---
title: "Stream movies to iPhone using a server."
date: 2010-06-19
forum: Multimedia Software
---

### Post by mondomunchies on 2010-06-19
I was wondering if it would be possible to set up a server on my desktop that has a folder of videos converted to iPhone formats that I can access with my iPhone over the internet to stream videos to my phone?

I started by setting up a server and used no-ip2 to create a domain name so I didn't have to worry about my dynamic ip changing.

Then I tried unsuccessfully to transcode a DVD to iPhone format using Arista, Transmaggedon, and Avidemux, none of which I could get to properly work.

Finally I used iUI ([http://code.google.com/p/iui/](http://code.google.com/p/iui/)) to create a site that would appear as a simple menu to search through my movies on my website and stream them.  This failed in that every time I set a static link it would change it to [http://mysite.com/___5__](http://mysite.com/___5__)  rather than [http://mysite.com/some_movie.m4v](http://mysite.com/some_movie.m4v)

Has anyone set up anything similar?  Any ideas?

---

### Post by mondomunchies on 2010-06-20
Ok I've gotten everything working pretty well.  I've switched to iWebKit for my web app look, the links all work properly.  Also I used Handbrake to successfully transcode my media.  The last hurdle is that when accessing my .m4v files over the internet with my iPhone, it tries to load the entire 1GB file before playing the movie.  How can I set it up to stream so that it buffers a portion at a time?  I guess this is the golden goose egg.  I guess this is why no one can support streaming video.  But I'm sure there is a way to do it.  It works for other videos.  Maybe if it was embedded?

---

### Post by mondomunchies on 2010-06-20
The thread about Handbrake: [http://ubuntuforums.org/showthread.php?t=1513507](http://ubuntuforums.org/showthread.php?t=1513507)
And the iWebKit site: [http://iwebkit.net/](http://iwebkit.net/)

---

### Post by mondomunchies on 2010-06-20
I wonder if I could configure GNUMP3d to do what I need?

---

### Post by prosonik on 2010-06-20
Why not just use the airvideo app and airvideo server, which works just great under ubuntu? The app is around $4 i think. 

Pro

---

### Post by mondomunchies on 2010-06-20
Doesn't that only work over your local wifi? I want to be able to access it anywhere using 3G. I'll look it up tho. I really don't know anything about it. Thanks.

---

### Post by mondomunchies on 2010-06-20
Apparently air video does what I was looking for from the beginning.  Thanks prosonik.

[http://ubuntuforums.org/showthread.php?t=1456417&highlight=air+video](http://ubuntuforums.org/showthread.php?t=1456417&highlight=air+video)

---

