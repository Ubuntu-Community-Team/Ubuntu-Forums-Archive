---
title: "turn black border areas of scanned book to white one"
date: 2011-07-22
forum: Multimedia Software
---

### Post by hyfanious on 2011-07-22
Hi
I just scanned a book recently
and as what happens in these situations , the borders get dark
I just looking for a simple way (prefer command line) to solve this problem
maybe, crop pictures for cutting out the borders and then change the dimension (**NOT MEAN STRETCH**) to regain original size
I am not sure , but any others ways that can turn black border areas to white one is fine with me,
what can I do?
tnx in advance ;)

---

### Post by hyfanious on 2011-07-22
I just figure out some method
I mention it here for sake of other people who may come across with same problem ;)
U must create a musk file with gimp or some other image editors with same size as ur photos like what i attached in here
then use this code in your shell
that's easy :)

first navigate ur shell to the folder that u store ur photos
then put ur mask file somewhere
then use this:
```

do composite -gravity north  /path/of/ur/mask/file/mask.png "$f"  "/path/that/u/want/save/new/files/$f.gif"; done;

```

---

