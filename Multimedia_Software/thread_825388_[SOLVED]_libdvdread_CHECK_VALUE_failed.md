---
title: "[SOLVED] libdvdread: CHECK_VALUE failed ???"
date: 2008-06-10
forum: Multimedia Software
---

### Post by bluepowder7 on 2008-06-10
so i'm using vobcopy in terminal to extract some vobs from a dvd onto my hard drive, and on quite a lot of discs i get this:

```

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1568 ***
*** for c_adt->cell_adr_table[i].vob_id <= c_adt->nr_of_vobs ***

```

it repeats a lot of times in a row (like 20+), then vobcopy does its thing and extracts the vob.  the vobs look to be in good shape if i try to play them in vlc, but it makes me worry that something just ain't right with my system.

---

### Post by mc4man on 2008-06-10
What command are you using for vobcopy?

---

### Post by bluepowder7 on 2008-06-10
vobcopy -o /mnt/sata_nas/vobcopy -l -t mymovie

---

### Post by mc4man on 2008-06-11
I wouldn't worry if your ripping that way to standalone vobs. If you were ripping to a video_ts it would be of concern. (Never seen that error even with structure protected titles, though I always rip to a full video_ts)

---

### Post by bluepowder7 on 2008-06-11
i assume i'm not losing any A/V info by going to a VOB instead of Video_TS, right?  the files are an intermediate short-term step since after i get a few VOBs on the hard drive, i run them through an H264 encoder to make smaller (600-1200meg) files for watching on the computer, and then blow away the VOB's to regain my space.

---

### Post by mc4man on 2008-06-11
No , the reason to use  -m in the command is to get a full working copy (menus, chapters, ect. ect.) if your encoding to H264 no need for all that.


Edit; if you ever wanted to a good basic command with version 1.1.0 or higher is
vobcopy -v -m -o /media/rips -F 16  (for one drive system) or
vobcopy -v -m -o /media/rips -F 16 /media/cdrom0   specifing input device
obviously -o /media/rips  is optional and needs to be adjusted to your output path

---

### Post by bluepowder7 on 2008-06-11
cool - thanks!  i'll just ignore the errors since they don't yet have an impact on the final encode.

---

