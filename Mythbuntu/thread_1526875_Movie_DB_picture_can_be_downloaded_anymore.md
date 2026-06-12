---
title: "Movie DB picture can be downloaded anymore"
date: 2010-07-08
forum: Mythbuntu
---

### Post by Powderking on 2010-07-08
Since some days the tmdb.py script isn't able to download cover and fan art anymore when i try to download metadata with the w key.

I checked the paths in MythTV and the storage groups. They're all correct and I have write permission too.

The script is working in the terminal and returns correct picture links.

I installed Jamu without any difference.
Maybe it's because I have the movies on a NFS share?

Does anybody have an ida what I should try?




Btw: When I scan for changes MythTV tells me:

Failed to Scan SG Video Hosts
...
If they no longer exist please remove them

How can I remove them?

---

### Post by SnafuFlux on 2010-07-08
I actually have the same problem to (no movie pics showing).

I have all my metaimages saved from my previous installation, but when I use the grabber (W key), it doesn't setup the paths nicely.  It just ignores the whole image portion.  I get the data (director, rating etc) but the images are just skipped.

the tv script is working fine, however.

is themoviedb.org having picture issues, or has something changed?

edit: to answer the above question of how to delete storage groups.  You need to go into mythsetup (mythbackend) and under the 6th option (Storage Groups) select each group you wish to delete and hit "d"

---

### Post by mdaitc on 2010-07-08
there's a bug that just got fixed to solve this problem with downloading new images.

[http://svn.mythtv.org/trac/ticket/8634](http://svn.mythtv.org/trac/ticket/8634)

build 25299 or later will have this fix in (at time of writing, mythbuntu were 25298 ) ....

---

### Post by Powderking on 2010-07-09
Thanks for the answers!

Since I'm not very familiar with these things I'm not sure what to do now. Should I download the file attached in the bug report and put it somewhere or should I just wait for the next update?
If it's better to wait how long would this be? I could download the cover art manually in the meantime.

I had the storage groups correct. And when I delete the storage group for videos it's still the same.
Maybe it's because I have added other directories with soft links?

---

### Post by Archmage on 2010-07-09
> **Powderking said:**
> Should I download the file attached in the bug report and put it somewhere or should I just wait for the next update?

Better wait for the next update - should be there within a few days.

---

### Post by Powderking on 2010-07-09
Ok, I will.

Thanks alot!

---

### Post by nickrout on 2010-07-09
> **mdaitc said:**
> there's a bug that just got fixed to solve this problem with downloading new images.

[http://svn.mythtv.org/trac/ticket/8634](http://svn.mythtv.org/trac/ticket/8634)

build 25299 or later will have this fix in (at time of writing, mythbuntu were 25298 ) ....

you keep saying that, but not everyone wants to risk trunk. Is this fix going into .23-fixes?

---

### Post by SnafuFlux on 2010-07-17
Bump...

does anyone know when this is going to be fixed for .23?  I really want posters to go along with my movies :D

---

### Post by SnafuFlux on 2010-07-17
as of .23 fixes build 25356, it has been fixed!

---

