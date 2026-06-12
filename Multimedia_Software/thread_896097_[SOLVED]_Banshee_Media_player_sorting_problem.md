---
title: "[SOLVED] Banshee Media player sorting problem"
date: 2008-08-20
forum: Multimedia Software
---

### Post by Minipalmer on 2008-08-20
I just installed Banshee Media player for my Ubuntu. I got it for the EQ and it's working great, except for one thing.

Banshee will only sort by tracks, and nothing else. Many of my songs don't even have a track labeled, so they are just bunched together randomly. I try to sort by artist, but it does not change.

The search also does not work. I don't know if these are connected or not.

---

### Post by Minipalmer on 2008-08-21
Fixed my own problem. But for those who search and find this thread...

The songs would not sort because when I installed Banshee it referenced its entire library from my Rythmbox library. Once I stripped the library clean and re-imported all my songs, everything worked fine.

---

### Post by boombox1387 on 2008-08-27
I'm having the exact same problem, but for me it happened when Banshee 1.2 tried to read from the old Banshee .13.2 database (not Rhythmbox).  I also found that clearing the database and re-importing everything took care of the problem, but I tend to obsess over things like play counts, so deleting my database and starting over is not my ideal solution.  I've filed a bug on Banshee's bugzilla but haven't gotten any response yet.  Has anyone else dealt with this and come up with any creative workarounds?

---

### Post by Cenoforums on 2008-09-24
Another note for those searching.
A easy way to reset banshee's media library is to delete the database all together. This will delete the cover art as well.
To do that check /home/user/.config/banshee-1 . In that folder theres a .db, delete that and problem over.
If you had a previous version of banshee installed, you will see a "banshee" folder in .config, delete the .db present in that folder as well, since banshee 1.0 will pick up the old version's database if it finds it.

---

### Post by boombox1387 on 2008-09-25
> **Cenoforums said:**
> Another note for those searching.
A easy way to reset banshee's media library is to delete the database all together. This will delete the cover art as well.
To do that check /home/user/.config/banshee-1 . In that folder theres a .db, delete that and problem over.
If you had a previous version of banshee installed, you will see a "banshee" folder in .config, delete the .db present in that folder as well, since banshee 1.0 will pick up the old version's database if it finds it.

Only do that if you want to lose all of your play counts, ratings, playlists, and other personal data.  If you really want banshee to create a new database for you, a much less permanent alternative is to move the banshee.db file to a different folder or simply rename it (to something like banshee.db.bak).

For anyone trying to avoid the database sorting problem mentioned in the original post, Banshee 1.3 fixes this.  The release is a bit less stable, though, so you may want to wait for the public 1.4 to come out.

---

### Post by smash4uf on 2008-10-27
I had the same problem, so deleted the library, re-added everything, now I can sort by whatever column I like, but the search will only look thru song titles, so even tho I have a lot of songs by 'Weezer,' if I search for 'Weezer' nothing will come up - this is a real pain, can anyone offer any advice?

Also - when I play videos it only plays the audio, and the screen stays black (all black, no Banshee logo in the middle)

Thanks,
Ashlyn

---

