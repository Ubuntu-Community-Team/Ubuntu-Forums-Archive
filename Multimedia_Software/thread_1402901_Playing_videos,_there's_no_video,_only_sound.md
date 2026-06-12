---
title: "Playing videos, there's no video, only sound"
date: 2010-02-09
forum: Multimedia Software
---

### Post by Eoghanalbar on 2010-02-09
This is true for .flv, .avi, .mov, and .mp4, at least.
This is true in both vlc and movie player.
Thumbnails generated from frames in the videos appear correctly in nautilus.
Videos play fine in firefox, on youtube, but I downloaded one as an .flv and then it had the same problem.
I have restricted extras freshly installed. My "Ubuntu 9.10 - the Karmic Koala" system is fully updated.
I've found several other forum posts about the same kind of problem, but I couldn't find anything helpful in them (like that the contrast setting might be WAY out of whack, which it wasn't, or that nvidia drivers needed to be updated or reinstalled, which I don't have anyway, etc).
Thanks to one helpful guy who responded the last time I posted this question I now have the w32codecs and libdvdcss2 from the Medibuntu repository installed, as well as the good, bad, and ugly gstreamer plugins. (I was under the misimpression that stuff came with the restricted extras.) Anyway, now those .wma files I've got kicking around work now, and I hadn't even gotten around to thinking about fixing THAT problem yet. :P
Unfortunately the video problem still exists, so I'm reposting this question, updated.
If anyone has any ideas what I should try next, I'd be much obliged!

Thanks!
Owen

---

### Post by gordintoronto on 2010-02-09
What is the video controller in your computer?  (lspci will tell you.)

Usually if youtube works, everything works!

---

### Post by Eoghanalbar on 2010-02-09
I am totally unfamiliar with this "lspci".
I put it into a terminal, copy-pasted the resulting data spew to a text file so I could search it for "video", but that word's not in there at all, apparently.

I did find this, which I think is probably what you mean?

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
```

Maybe this is related: when I tried ubuntu on this same computer years ago I could use all those fancy visual effects (beryl/compiz or whatever it was called back then), but now my desktop effects are set at "none" and I can't even enable "normal" effects.  (The only restricted driver I could enable under system>administration is a "software modem", no video cards.)

---

### Post by gordintoronto on 2010-02-09
Good work!  Your computer has an Intel 945 video adapter.  I have heard it has issues in 9.10, but I don't know the details.

---

### Post by Eoghanalbar on 2010-03-23
By the way, I finally figured out what was causing this.

I'm running dual head monitors. The one in the laptop, and an old LCD off to the side. Ya know, as one, long, continuous desktop.

If I turn one or the other off, or set them to "mirror screen" rather than extended, the video shows up normally.

This is still annoying, but at least it's working.

---

### Post by gordintoronto on 2010-03-24
Thanks for letting people know! Perhaps you could mark the thread as "solved"?

---

### Post by Eoghanalbar on 2010-03-24
...You know, I don't actually know how. :P

Also, while I do think you're right, I should change it to aid potential future people with the same problem in their search, I gotta say that it is only partly solved, still.

---

### Post by mumuyazzer13 on 2010-03-24
Good work

;);););););)

---

