---
title: "Mounting an 8GB iso file"
date: 2009-05-27
forum: Mythbuntu
---

### Post by Caps18 on 2009-05-27
I tried using the mount command with -o loop -t udf, and I can't seem to be able to access the files in this ISO file.  I tried a few different file types (most of the list in 'man mount').  Is there a different filesystem type for high capacity DVDs?  Is there any program that will work in Mythbuntu that would allow me to open this? 

Thanks

---

### Post by murchball on 2009-05-27
[FONT="Arial"]Try this:

```
sudo mount /home/username/image.iso /mnt/media -t iso9660 -o loop
```

Use single quotes if you have any spaces in the path[/FONT]

---

### Post by utar on 2009-05-28
> **Caps18 said:**
> I tried using the mount command with -o loop -t udf, and I can't seem to be able to access the files in this ISO file.  I tried a few different file types (most of the list in 'man mount').  Is there a different filesystem type for high capacity DVDs?  Is there any program that will work in Mythbuntu that would allow me to open this? 

Thanks

As a matter of interest why do you want to mount the image?  If it is a DVD iso Myth will play the iso file directly.


Utar

---

### Post by cb951303 on 2009-05-28
Did you try: Right Click > Archive Mounter
EDIT: Oh I'm sorry you're using 7.10

---

