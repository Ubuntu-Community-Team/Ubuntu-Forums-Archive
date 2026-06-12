---
title: "copy dvd to iso"
date: 2012-03-18
forum: Multimedia Software
---

### Post by marienvuik on 2012-03-18
I used to be able to just right click on a dvd folder on the desktop and select copy and copy the dvd to iso.
I stopped using ubuntu for a year and suddenly this does not work any more.Do i need to downgrade to 9.4 or so.
I do have the medibuntu repo s installed.
Any help will be much apreciated.

---

### Post by andrew.46 on 2012-03-18
I am not sure what the problem is on your system but if the dvd is not encrypted you can use some variation of the following:

```

dd if=/dev/dvd of=my_filename.iso bs=2048

```

where of course you change the name of *my_filename.iso* to suit your own needs. This will not work with an encrypted dvd but there are other strategies for these.

---

