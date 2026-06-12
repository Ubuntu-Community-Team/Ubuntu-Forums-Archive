---
title: "How to get IMDB data for multiple movies at a time?"
date: 2008-08-02
forum: Mythbuntu
---

### Post by bmwman on 2008-08-02
I have over 5-600 movies and i like to see all the ratings, poster, etc that comes from IMDB. I've done it all one by one but it really takes a long long time. Then I need to do that on 3 different frontends. Is there a faster way or can that be done automatically instead of on by one?

Thanks for suggestions

---

### Post by tgm4883 on 2008-08-02
Yea there is a bulk updater script.  I'm working on getting it included in Mythbuntu.

Theres a readme in there that should help you get what you want.  After extracting it to the right place, I run this

/usr/share/mythtv/mythvideo/scripts/imdb-bulk-update.pl -N -Dupskip -Exclude -Host HOSTNAME -Password "PASSWORD"

---

### Post by bmwman on 2008-08-02
I think i've tried it before but I couldn't figure it out. I play with it later and hopefully I'll get it to work this time :)

---

### Post by bmwman on 2008-08-05
Is there a way to make it work if the movies is two parts, named either Movie-cd1 and Movie-cd2 or Movie-part1 and Movie-part2?

It can't find those and I have quite a few.
Thanks in advance

---

### Post by toorima on 2008-08-08
> **bmwman said:**
> Is there a way to make it work if the movies is two parts, named either Movie-cd1 and Movie-cd2 or Movie-part1 and Movie-part2?

It can't find those and I have quite a few.
Thanks in advance

Its the "cd" that makes it not work, so either rename the movie to movie.1.avi and movie.2.avi and it will work, or merge the 2 parts. I do it all the time with my xvid's
mencoder -forceidx -ovc copy -oac copy -o movie.avi movie.1.avi movie.2.avi

---

