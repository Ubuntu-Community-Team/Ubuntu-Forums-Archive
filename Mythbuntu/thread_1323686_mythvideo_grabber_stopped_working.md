---
title: "mythvideo grabber stopped working?"
date: 2009-11-11
forum: Mythbuntu
---

### Post by SnafuFlux on 2009-11-11
about a week ago it worked wonderfully.  now only tv grabber works, movie fails every time.  Usually with the error that it can't contact themoviedb.org.  But I can browse to it just fine.

Anyone else having issues or could point me in the right direction?

edit: I'm using mythbuntu 9.10 fully uptodate

---

### Post by Al_Vampyre on 2009-11-12
Same issue here, just noticed it last night.

---

### Post by liquidox on 2009-11-12
Finally found this thread, same problem here, they must have changed something today or yesterday, worked fine for me last Tuesday.

> Unable to contact themoviedb.org while retrieving movie list, stopped at ./tmdb.pl line 286.

---

### Post by liquidox on 2009-11-12
I think here lies the problem:

[http://forums.themoviedb.org/post/3169/#p3169](http://forums.themoviedb.org/post/3169/#p3169)

> New records are working fine, but it's the same situation. Any title that was searched for in the weird zone is cached broken. We have to wait for those records to purge and everything will magically fix itself.

---

### Post by SnafuFlux on 2009-11-12
[http://www.themoviedb.org/content/Donate](http://www.themoviedb.org/content/Donate)

---

### Post by liquidox on 2009-11-12
That's a bit silly, read the link I posted before, the API breaking is not related to bandwidth/hosting.

Also they are working on a better TMDB, read this:

[http://forums.themoviedb.org/topic/698/tmdb-v2/](http://forums.themoviedb.org/topic/698/tmdb-v2/)

I've donated before nonetheless, it's a great service.

---

### Post by SnafuFlux on 2009-11-12
> **liquidox said:**
> That's a bit silly, read the link I posted before, the API breaking is not related to bandwidth/hosting.

Also they are working on a better TMDB, read this:

[http://forums.themoviedb.org/topic/698/tmdb-v2/](http://forums.themoviedb.org/topic/698/tmdb-v2/)

I've donated before nonetheless, it's a great service.

I posted before I had a chance to read it ;)

I agree, your information is much more accurate than mine.  I'm not at home to test the 2.0 api.  Are you?

either way, I will donate tonight!

---

### Post by liquidox on 2009-11-12
Not sure what you mean, tmdb.pl uses the 2.0 API, not to be confused with TMDBv2. And what I pasted earlier is the current tmdb.pl error.

But as the thread said, it should fix itself the coming day(s).

---

### Post by SnafuFlux on 2009-11-12
I wasn't referring to tdmbv2.  I was talking about api2.0(tmdb.pl).

the thread you posted says 
> OK, I think everything's working again but **records that were accessed in the weird zone were cached as such**. I have no easy way of clearing those records so we'll just have to wait the ~20 hours for the records to purge.

I was thinking we could test to see if the api 2.0 is working by trying a few movies and hoping they weren't already accessed during the "weird zone".  But this would be nearly impossible to guess a movie that wasn't accessed during this period.

That's all I meant.

---

### Post by liquidox on 2009-11-13
Problem solved, for the record.

---

### Post by SnafuFlux on 2009-11-13
agreed!  nice to have it back

---

