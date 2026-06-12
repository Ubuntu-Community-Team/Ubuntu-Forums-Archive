---
title: "1:1 DVD Backup Program?"
date: 2009-08-20
forum: Multimedia Software
---

### Post by Incarnadine on 2009-08-20
On my Windows PC I am using AnyDVD to backup my DVDs, but I enjoy using Linux much more and would like to backup DVDs on it as well. I have no idea though what software to pick from the repository. Do you have any favorites? I was thinking about using AnyDVD via Wine, but I'm saving that as a last resort. Thanks for the help :popcorn:

---

### Post by zwierbel on 2009-08-20
maybe: k9copy

---

### Post by kpkeerthi on 2009-08-20
```

vobcopy -m

```
The command **m**irrors the whole dvd to harddisk. It will create a directory named after the dvd and copy the ifo, bup and vob files there. The title-vobs are decrypted during this. 

For more info, see ```
man vobcopy
```

---

### Post by stinger30au on 2009-08-20
k9copy will do it

sudo apt-get install k9copy

once installed, open up the settings menu and tell it what size dvd u want it to record to, be it 4 or 8 gig and what native language u want it to use

---

### Post by Incarnadine on 2011-09-06
I recently found that Brasero and Medibuntu in combination work really well for backing-up DVDs.

Thanks for the feedback and advice guys:popcorn:

---

