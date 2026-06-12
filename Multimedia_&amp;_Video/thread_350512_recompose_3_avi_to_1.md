---
title: "recompose 3 avi to 1"
date: 2007-01-31
forum: Multimedia &amp; Video
---

### Post by rcmn on 2007-01-31
i'm looking for a tool or an how to that would let me rebuild 3 separates files avi(700mg) to 1 single file. i was thinking i could find this easily but i'm not succeeding so any pointers would help.thx

---

### Post by taurus on 2007-01-31
You mean something like

```
avimerge -o filename.avi -i first_file.avi second_file.avi third_file.avi
```

---

### Post by yabbadabbadont on 2007-01-31
> **taurus said:**
> You mean something like

```
avimerge -o filename.avi -i first_file.avi second_file.avi third_file.avi
```

You didn't tell him which package provides that tool...  :D

---

### Post by RomeReactor on 2007-01-31
Try AviDemux, look for it in Synaptic or Adept, or:

```
sudo apt-get install avidemux
```

---

### Post by rcmn on 2007-02-01
i have avidemux installed. perfecto thx guys !!!

---

### Post by rcmn on 2007-02-01
ok so after trying avidemux for the 2nd time i finally decided to use avimerge.If u look for Avimerge in adept,synaptic,etc.. it won't show up.But it will be installed by Transcode(by a dependencie or part of it i didn't look too much).anyway it's merging now.thx

---

