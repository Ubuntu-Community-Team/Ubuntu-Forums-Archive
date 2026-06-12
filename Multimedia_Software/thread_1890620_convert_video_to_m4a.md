---
title: "convert video to m4a"
date: 2011-12-03
forum: Multimedia Software
---

### Post by neerg21 on 2011-12-03
Hello,

I've been having trouble getting my sony walkman to display album art for mp3's transferred. I noticed that an m4a file that I transferred retained its album art when synced to the walkman.

Is there any program that can convert mp3s to m4a files available for ubuntu/linux.

Thanks,

Neerg21

---

### Post by staf0048 on 2011-12-03
I don't think you need to go through that much trouble.  The issue is more than likely that your album art is simply not written to the actual mp3 files, therefore, when you transfer it there's nothing to display.

Are you using Banshee?

---

### Post by hansdown on 2011-12-03
Hi,neerg21.

Try 

```
arista 
```

It's in software center, and synaptic.

Edit;

staf0048, is right about that.

---

### Post by neerg21 on 2011-12-03
Thanks for the replies!

I should have mentioned that i had the songs from my windows days and the album info and art were embedded into the mp3 file using mp3 tag, and I am using banshee, and I've tried other major programs as well and drag and drop, nothing seems to work

---

### Post by staf0048 on 2011-12-03
Hmm...

Ok, well I'll give you the tip I was thinking of before, though I'm not sure if it will make a difference.

In Banshee, click on Edit/Preferences and make sure the "write metadata to files" checkbox is marked.  Mine came unchecked by default, and once I marked this option, Banshee went through my whole library and (ta da), all my album art was there.

If that doesn't work, you can try ffmpeg.  There is a gui front end to it called winff (I beleive).  This program can transfer any media file type to any other.

Good luck!

---

### Post by neerg21 on 2011-12-03
Thanks for getting back to me,

The strange this is that all my album art is in banshee as well as when i plug my walkman in I can see the album art on each individual file, its just on the actual mp3 player itself that it doesn't show up. I'll give that program a try though.

Thanks!

---

