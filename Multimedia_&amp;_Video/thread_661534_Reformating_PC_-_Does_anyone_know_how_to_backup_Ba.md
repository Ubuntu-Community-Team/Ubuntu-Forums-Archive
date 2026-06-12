---
title: "Reformating PC - Does anyone know how to backup Banshee database (raitings)"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by Mysticle31 on 2008-01-08
Surprisingly, there doesn't seem to be much on this.

I'm going to be reformatting my computer here soon and I would like to backup my Banshee database.  Specifically my ratings.  Podcasts would be nice, but what I really need are the raitings.  

I painstakingly went and listened to my whole collection and raited the songs.  It actually helped me streamline my collection as I was able to remove all my one star songs.  Anyhow, I would like to back this up.

Any ideas?

---

### Post by moderatelymodest on 2008-01-08
I haven't used banshee much, but for all my setting backups I just copy the ".[program name]" directory from my home directory.

So I would look at ~/.banshee and see if it contains the stuff that you want to keep.

---

### Post by Mysticle31 on 2008-01-08
Hmm..  I never thought of that.  

I'll have to remember that for other programs.

Unfortunately, there isn't a .banshee.

I think it uses a MySQL database.  As I recall it asked me what type of database I would like to use when I installed it.  However, I have played with several media apps, I could be thinking of another.

---

### Post by gsiliceo on 2008-01-09
Banshee.db it is in /home/YOURUSERNAME/.config/banshee you better save the entire folder because it contains your plugins, downloaded lyrics and album covers.
By the way after reinstalling, you need to change those folders and subfolders to the current user, you know right click in banshee folder, properties, permissions.
Tested in gutsy.

---

### Post by Mysticle31 on 2008-01-09
Awesome!  Thank you.  That worked quite well.:guitar:

---

