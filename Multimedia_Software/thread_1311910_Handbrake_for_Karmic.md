---
title: "Handbrake for Karmic"
date: 2009-11-02
forum: Multimedia Software
---

### Post by andied on 2009-11-02
There is a new Handbrake svn2907 available for Karmic and it works fine for me, but on a test I made, it takes approx 14% longer in Karmic 64 than XP. I noticed that HB only uses about 75% of my cpu(s) (dual core), even when I forced the cpu to max performance rather than "Ondemand". XP uses around 95%-100% of my cpu(s). Is there a way to make an app like HB use more cpu?

---

### Post by JohnAStebbins on 2009-11-04
The performance issue is likely the linux scheduler problem that the x264 developers found.  It's been fixed in the 2.6.32 kernel.

See [http://x264dev.multimedia.cx/?p=185](http://x264dev.multimedia.cx/?p=185)

---

### Post by andied on 2009-11-04
Thanks for the info, John.

---

### Post by Vadi on 2009-11-04
Is there a .deb available or did you get it from handbrake svn?

---

### Post by andied on 2009-11-04
[http://handbrake.fr/snapshot.php](http://handbrake.fr/snapshot.php)

---

### Post by Vadi on 2009-11-05
Thank you.

---

