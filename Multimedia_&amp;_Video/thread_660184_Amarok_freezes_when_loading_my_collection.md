---
title: "Amarok freezes when loading my collection"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by dgreich on 2008-01-06
I have about 4000 songs in my collection I've had from over the years. I have it on a portable hard drive I use when on the go on my laptop with Linux Mint 4.0 on it-  Amarok loaded it 100% fine with no problem.

On my home desktop, I have Ubuntu Gutsy amd64 installed-  however, I can not load the collection up.  It gets to about 59% and just freezes.  Not a hard freeze- the loading just sits there at 59%.  I even let it sit overnight, and it can not get past 59% at all.  I've restarted numerous times, removed Amarok and reinstalled, even deleted all of my settings in Ubuntu-  nothing.  Will not load.

The hard drive is NTFS, but like I said- it works fine on my Linux Mint machine which is pretty much Ubuntu (except 32-bit instead of 64 I have at home) :confused:

I'd like to get this figured out so I can go onto my final obstacle to take- syncing my Xbox 360 media center with my system... then its goodbye Windows!

---

### Post by xens on 2008-01-06
I had the same problem few month ago, I had to remove my personal settings in /home/user/.kde/share/apps/amarok. Be careful removing these files will remove your settings in amarok (covers, + have to rescan collection)

---

### Post by dgreich on 2008-01-06
> **xens said:**
> I had the same problem few month ago, I had to remove my personal settings in /home/user/.kde/share/apps/amarok. Be careful removing these files will remove your settings in amarok (covers, + have to rescan collection)Nope.  Still stuck at 59% :(

---

### Post by xens on 2008-01-07
if you launch amarok from the console, can you see some error messages ?

---

### Post by dgreich on 2008-02-02
How would I launch it from command line, and what would I do to let it build my collection?

---

### Post by dgreich on 2008-02-08
bump??

still gets stuck at 60%... :(

---

### Post by slamgauge on 2008-02-14
Bump 

I get the same freeze and it kills me.
I want amarok to work :(

---

### Post by dgreich on 2008-02-14
So I figured it out... well, the Amarok forums figured it out.  Basically, you need to open the Amarok log file when it freezes and it will show what song is trying to load.  That is the song giving it trouble.

[http://amarok.kde.org/forum/index.php/topic,15012.msg21652.html#msg21652](http://amarok.kde.org/forum/index.php/topic,15012.msg21652.html#msg21652)
> That's right. This problem has been posted, but it is not well defined on faq. Amarok do not finish its build, in fact. Reading the explanation of the problem on faq, one could believe it finishes the building proccess. So, as it is posted on faq, may cause confusion, for newbies. I believe it can be useful to copy the pointed solution (it works to me!), so, here it goes:
Look at the file***_ ~/.kde/share/apps/amarok/collection_scan.log_***. It should contain single file name. If that name does not change for some time, try moving the file out of your collection directory and restart the scan.

---

