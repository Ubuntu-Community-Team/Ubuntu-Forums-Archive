---
title: "peculiar rhythmbox problem"
date: 2008-06-08
forum: Multimedia Software
---

### Post by fontenot_1031 on 2008-06-08
I just did a trunk build of rhythmbox through svn so that I could compile it with mtp support. At first when I tried to run it the program said that it couldn't find librhythmbox-core.so.0 so I downloaded the stable rhythmbox.deb file and extracted only the librhythmbox-core files and moved them to /usr/lib myself. Now when I run rhythmbox from the terminal I get this error
```
rhythmbox: symbol lookup error: rhythmbox: undefined symbol: rb_marshal_BOOLEAN__STRING_BOOLEAN

```
any ideas?

---

### Post by Kropotkin on 2008-08-23
I just compiled v0.11.6, and I see this error message when I try to start rhymthmbox. Did you find a solution?

Thanks.

---

### Post by Benjamin_Lebsanft on 2008-09-03
Uninstall via Synaptic and do the make install command again, worked for me.

---

### Post by seapine on 2008-09-05
> **fontenot_1031 said:**
> I just did a trunk build of rhythmbox through svn so that I could compile it with mtp support. At first when I tried to run it the program said that it couldn't find librhythmbox-core.so.0 so I downloaded the stable rhythmbox.deb file and extracted only the librhythmbox-core files and moved them to /usr/lib myself. Now when I run rhythmbox from the terminal I get this error
```
rhythmbox: symbol lookup error: rhythmbox: undefined symbol: rb_marshal_BOOLEAN__STRING_BOOLEAN

```
any ideas?

try this:
```
sudo cp /usr/local/lib/librhythmbox-core.so.0 /usr/lib
```

---

