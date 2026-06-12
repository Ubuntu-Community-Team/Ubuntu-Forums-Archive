---
title: "software to edit and mount isos"
date: 2006-12-26
forum: Multimedia &amp; Video
---

### Post by ukasz20 on 2006-12-26
hi

i am looking for a software to mount and edit if possible iso images.

---

### Post by invalid on 2006-12-26
Mounting:
```
sudo mkdir /media/iso
sudo modprobe loop
sudo mount file.iso /media/iso/ -t iso9660 -o loop
```

Editing, as far as I know, requires more than just an ISO.

---

### Post by ukasz20 on 2006-12-26
it is only working for mounting i can not edit files

---

### Post by invalid on 2006-12-27
What kind of ISO is this you are mounting? And what is it you are tying to edit? The ISO itself. or the files which the ISO deploy when it is mounted?

---

### Post by ukasz20 on 2006-12-28
i want to edit files that are within iso image

---

### Post by paziek on 2006-12-28
You cant edit iso image.
You can mount it, copy its contents, edit them and make a new iso image.

There are programs that do that automatically for you, but I know only ones for windows :s

---

### Post by MetalMusicAddict on 2006-12-28
For editing ISO's try ISO Master 0.6. Theres a .deb on [THIS]("http://www.getdeb.net/category.php?id=4") page.

---

### Post by paziek on 2006-12-28
Found that app as well, while googlin ;-)

Heres another link for .deb

[http://littlesvr.ca/isomaster/downloads.php]("http://littlesvr.ca/isomaster/downloads.php")

---

### Post by ukasz20 on 2006-12-29
ok thx guys it is working

---

