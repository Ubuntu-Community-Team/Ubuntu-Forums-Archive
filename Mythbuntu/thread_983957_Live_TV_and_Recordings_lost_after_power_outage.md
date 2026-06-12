---
title: "Live TV and Recordings lost after power outage"
date: 2008-11-16
forum: Mythbuntu
---

### Post by Crusty Juggler on 2008-11-16
I had my Mythbuntu system on tonight when the power went off a couple of times inside of 5 mins.  I shut everything down until the storm was over, but now, something is wrong in that I can't watch Live TV and my Media Library shows no recordings. "Watch Videos" works fine and all my videos are there.  And when I go to Mythbuntu set up, it is detecting my tuner just fine. 

I'm pretty sure this is just a minor thing, like somehow permissions got changed or something.  I had this happen once before, but I just reinstalled Mythbuntu.  I have a lot of recordings saved at this point, so I don't really want to go down that road again.

Any help would be greatly appreciated.

---

### Post by volkswagner on 2008-11-16
You can try to repair the database.  There is a tool built into mythbuntu-control-centre to allow this.  It is toward the bottom of the choices on the left, I think it is labeled advanced options or similar.

---

### Post by Nikas on 2008-11-16
Run this via SSH:
```
perl /usr/share/doc/mythtv-backend/contrib/optimize_mythdb.pl
```

---

