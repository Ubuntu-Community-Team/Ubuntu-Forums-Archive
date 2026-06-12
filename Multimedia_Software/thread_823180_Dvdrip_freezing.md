---
title: "Dvd::rip freezing"
date: 2008-06-09
forum: Multimedia Software
---

### Post by xravexheavenx on 2008-06-09
Well, for some reason dvd::rip is freezing on transcode.  I can't quite figure it out.  The rip is fine before the transcode to XviD but for some reason it will freeze on random intervals.  The entire program is not freezing but the transcode stops completely.  Any ideas?

---

### Post by slightcrazed on 2008-06-28
I'm seeing this same behavior in cluster mode with 2 pass encoding.... sometimes it finishes fine, other times it will stall during a pass, and then the whole job is pretty much lost (although I've had success with canceling the project, manually running the command that failed, and then picking up where it left off). 

Heat perhaps? Or a bad rip?

---

### Post by keller.baum on 2008-09-22
I'm having the same problem seemingly at random.  Some transcodes will work & then some fail consistently at 99.97% on the first pass.

---

### Post by RRNovaes on 2008-12-31
I am experiencing the same problem.
Transcoding freezes somewhere between 85% and 95% on the first pass every time.

Any ideas?

---

### Post by SuperSonic4 on 2008-12-31
You could use k9copy, it is a native KDE app too
What's the error code if you run it in terminal?

---

### Post by ruddha on 2009-01-01
Or try handbrake:
[http://handbrake.fr/](http://handbrake.fr/)

---

### Post by Tykin on 2009-01-12
I've also had problems with this while burning certain dvds. 
At first, I thought the problem had to do with hard drive space, but I increased the Ubuntu partition to no avail.

I also don't think the length of the movie is a factor, since I've had dvd::rip succeed and fail on both 22 minute episodes and full-length movies.

I think it has more to do with the dvd's encryption type than anything else. Of course, I am unfamiliar with Perl so I have no idea how dvd::rip decodes the vob files (maybe someone else can enlighten us :) ). 

If someone could let me know how to check DVD encryption types, I can get back to you about whether or not there's a correlation.

---

### Post by Tykin on 2009-01-12
Just wanted to add that a decent alternative is Thoggen, which will convert to ogg with a theora video codec. 

You can then use mencoder to covert from the ogg to an xvid based avi.

This is kind of a roundabout approach and it doesn't have all the options of dvd::rip, so I'd much rather figure out why dvd::rip is freezing.

---

