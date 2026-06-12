---
title: "Region or Disc Problem? European Double Sided DVD not playing"
date: 2009-01-14
forum: Multimedia Software
---

### Post by BastardNamban on 2009-01-14
I have been looking in the forums, and I'm just not quite sure what to do here...

I got a DVD from Glashutte in Germany in the mail a few days ago, a special PR double sided DVD (one side marked PAL, the other side marked NTSC, same thing on both sides for easier playback around the world I guess) that is recognized in my 8.04 Ubuntu. The DVD icon shows up on my desktop with the name Glashutte in it, so it recognizes the disk. I know there are 2 tracks on either DVD side, both the same things. The case it came in has "DVD 10 * PAL/NTSC * Code 0 * Deutsch/English * Dolby Digital 2.0" written on the back.

Problem is, it opens the DVD- no picture, no sound, and as a track that's only 1 second long. I can't seem to figure out what to make of this response- it's not refusing to read the DVD, but nothing happens.

I tried browsing the data on the DVD- the AUDIO_TS folder has nothing in it, and the VIDEO_TS folder has 16 things, one of which is what looks like a menu video (.vob) that plays- it doesn't go anywhere or let me select anything in the menu.

What am I missing here? I'm having a lot of DVD issues since I switched to ubuntu...I've tried reading FAQs and following what advice I could, but no avail. I even tried burning an .ISO with Brazero and it doesn't even spin up in my drive- it won't read at all.

PS: before I left XP, I think I region switched my DVD drive to region 2 from region 1 to watch Japanese movies (where I live now), and don't remember switching back before I converted.... I installed regionset if I need to change region. Can Linux bypass region settings in hardware? I hate that I only have 4 switches and then my drive is forever fixed.

---

### Post by BastardNamban on 2009-01-23
Really no ideas? I still can't get the thing to work. Anyone? Or am I missing something so obvious that everyone thinks I'm an idiot and thus refuses to post?

---

### Post by Hilko on 2009-02-03
I had similar problems: Got this DVD wich is set for all regions 1,2,3,4,5,6,7,8. But it just wouldn't play. I tried everything i could find on the forums; vlc, totem, libdvdcss, and setting the region of my DVD player using regionset. Nothing worked.

Finally i managed to copy the disk to my hard drive using   ```
sudo cp -R /mydrivename /directoryname
```

then i had to change the permissions
```
sudo chmod -R 755 /directoryname
```

and then with VLC --> open directory I can now play the content from my harddrive.

---

