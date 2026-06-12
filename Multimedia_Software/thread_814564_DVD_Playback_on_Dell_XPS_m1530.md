---
title: "DVD Playback on Dell XPS m1530"
date: 2008-05-31
forum: Multimedia Software
---

### Post by lemboy4 on 2008-05-31
Hi all, this isn't a question, it's just a post to possibly help others facing this problem.

I recently purchased the fairly-popular Dell XPS m1530 laptop and could not get ANY DVD playback, even after installing every codec (Medibuntu, etc) I found.  VLC crashed immediately after startup, Totem said "Unable to read resource" or something similar, and every other media player failed in some fashion of its own.  I searched Google and the forum posts here and found many people with similar-sounding problems (down to the exact error VLC was throwing).

Anyway, the problem turned out to be the drive, which is a MATSHITA DVD +/- RW.  You can check your drive via:
sudo hdparm -i /dev/dvd
The drive was set by default to region mask 0xFF, which I think is meaningless (region 0?).  And, from Google, I gathered that Matshita drives are especially unforgiving with DVDs that do not match the region for which they are intended.

If you only have DVDs from one region, like I do, simply download regionset:
sudo apt-get install regionset
and tell it to set your drive's region to whatever you need!  That's all, but it took me many hours to figure it out.

---

### Post by damis648 on 2008-05-31
Interesting. Seems that some M1530s ship with this "MATSHITA"... mine has a Optiarc DVD+/-RW AD-7640A. Wierd.

---

### Post by rbfthomas on 2009-02-21
Thanks!  This was just the ticket for my XPS m1530.  I'd installed and re-re-reinstalled libdvdcss2 and all the rest, but this did the trick.

Just a couple of additional "for dummies" points:

after installing the regionset package, you have to run it:
sudo regionset

Region 1 is the US & Canada, the full listing is [here]("http://en.wikipedia.org/wiki/DVD_region_code").

My machine required a restart afterwards, possibly because it's such a low-level setting.

Again, I appreciate your posting what you learned - it saved me a lot of headache!

---

