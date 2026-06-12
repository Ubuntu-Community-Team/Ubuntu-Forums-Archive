---
title: "Cant Delete Recordings"
date: 2008-08-18
forum: Mythbuntu
---

### Post by rubrboots on 2008-08-18
have just set up a mythbuntu 8.04.1 frontend/backend, I have a seperate disk for recordings. Everything works properly except that I 2 files in my recordings that I can not delete. I think they were created while I was testing and before default recording location/permissions were set. my backend log is below 

```
2008-08-18 14:19:20.564 Error deleting '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv/4294967295_20080818000525.mpg': No such file or directory
```

I dont care if the files are actually deleted, but I dont want them to show up in my list of recordings.

---

### Post by newlinux on 2008-08-18
The files are probably gone, myth just doesn't know it. easiest thing to do is to cd into your recordings directory and type:

```

touch 4294967295_20080818000525.mpg

```
or whatever the filenames are that can't be deleted and then try deleting them again. Or you could modify the DB, but this is probably all you need to do.

---

### Post by rubrboots on 2008-08-19
That worked! Thanks for the help:)

---

