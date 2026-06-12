---
title: "Creative Zen W gnomad2 Segmentation Fault"
date: 2007-09-16
forum: Multimedia &amp; Video
---

### Post by alinuxfan on 2007-09-16
when I run gnomad2 (version 2.9.0 in gutsy) it will sometimes quit while transferring files.  So I decided to run it from the command line and:
```
adam@desktop:~$ gnomad2
PTP: Opening session
Queried Creative ZEN Vision W
ID3v2 TLEN tag time was 0
Segmentation fault (core dumped)

```

Anyone know why it is coming up like that?  Do I have a bunch of corrupted files on my Zen?  Something about the !D3v2 Tag?
/shrug

---

### Post by eOgas on 2008-02-19
I know it's kind of late, but I had this same problem today.  I found that if I go into the preferences and uncheck "Write ID3v1/v2 tag to files transferred to harddisk" it works fine.  I still have no idea how this will affect the files, it's still transferring.  I'm assuming that they should play fine just with no ID3 tags.

---

