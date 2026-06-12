---
title: "amarok database problem"
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by Naegling23 on 2007-07-07
Ok, so Im running the latest version of amarok 1.4.6 and it has become unusable suddenly.  I added some new songs to my library, and it began to update the database....for three straight days.  I've tried removing the song's I added, but still no luck.  While the database updates, amarok is locked up and unusable.  Any idea how to fix this?

---

### Post by Zachy on 2007-07-09
I'm no Linux/kde/AmaroK/computer expert but you could try removing ~/.kde/share/apps/amarok/. Just make sure to backup the folder first, in case you want to undo it. Also you shouldn't have AmaroK running while doing it.

Hope it helps!

Zachy

---

### Post by propensity on 2007-07-10
> Ok, so Im running the latest version of amarok 1.4.6 and it has become unusable suddenly. I added some new songs to my library, and it began to update the database....for three straight days. I've tried removing the song's I added, but still no luck. While the database updates, amarok is locked up and unusable. Any idea how to fix this?

I had the same problem. Don't delete the whole ~/.kde/share/apps/amarok/, if you haven't done so till now. Just delete collection.db and amarok will build a new collection for you. However, you will lose song ratings, stats, and cached lyrics :(.

If you delete the whole folder, you will lose album cover, scripts, playlists, themes as well.

---

### Post by Naegling23 on 2007-07-13
propensity, that is exactly what I did, worked great.

I think the latest upgrade for amarok changed the database structure somehow, regenerating it fixed everything.

Im now back to having the best media player for any OS!

---

### Post by ginsujim on 2007-08-04
thanks for the advice I was having the same problem and this worked perfectly to resolve it.  I think the forums are great, every problem I've had I've been able to fix due to this great community.  Hopefully I'll eventaully know enough to help too but for now thanks.

---

### Post by etienner on 2008-04-04
I've got the same problem (duplicate song in the collection, amarok usign all the time lot of CPU for collection scanning), but I do not whant to loose all the statistics, ratings, lyrcs, ... Is there a way to solve this?

---

