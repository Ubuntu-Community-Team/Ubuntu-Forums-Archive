---
title: "Move F-Spot photos directory?"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by joeljkp on 2007-11-12
Hi all.

I just installed Gutsy and restored a backup from Feisty. Basically, I was using F-Spot to manage my photos from its default Photos directory. But now that Gutsy likes using Pictures (it's just a name, I know), I want to move the F-Spot photos folder to that.

Is there a way to tell F-Spot that all my pictures are now in Pictures instead of Photos? I thought of importing them again after setting the default directory, but then it seems like I'd lose my tags.

Any ideas?

---

### Post by solar george on 2007-11-13
Set the default directory and then rename Photos to Pictures

---

### Post by joeljkp on 2007-11-13
Hi, thanks for the reply. I ended up finding out that for JPEGs anyway F-Spot stores the tags in the files themselves. So I just import from Photos to Pictures and it worked fine.

---

### Post by firefeather on 2008-03-16
Using [this post]("http://ubuntuforums.org/showthread.php?t=254674&p=1493045"), I did the following commands after going into the .gnome2/f-spot/ directory:
```
sqlite ./photos.db .dump > f-spot.dump
mv ./photos.db photos.db.backup
gksudo gedit ./f-spot.dump
sqlite ~/.gnome2/f-spot/photos.db < f-spot.dump
```

In gedit, I did a find-and-replace for the old directory name and replaced it with the new one. This helped me to fix my F-Spot photos after changing the name of my home directory. My F-spot tags had *not* been set to save in the file, and this was how I fixed it.

---

