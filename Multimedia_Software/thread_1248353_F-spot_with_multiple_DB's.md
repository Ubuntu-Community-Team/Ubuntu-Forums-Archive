---
title: "F-spot with multiple DB's"
date: 2009-08-24
forum: Multimedia Software
---

### Post by seanlano on 2009-08-24
I have bought a new DSLR (a Pentax K7), and love taking lots of pictures with it. Before I had my new camera, I didn't take as many pictures. I used to import the pictures with F-spot into /home/shared/Pictures (a directory I set up) and have the F-spot db at /home/shared/f-spot, and each user in my family had links from their local F-spot folder/db to the shared one, so that everyone had the same pictures and tags. 

However, now that I take a lot of (often fairly pointless:)) pictures, the rest of the family don't really want to see most of them, except the ones I take of the family. I tried using digiKam to manage my photos, alongside F-spot for the family photos, but I find digiKam a bit too different, and I would prefer to use F-spot. 

I would like to run one instance of F-spot with the shared db, and another instance with my own, personal db.  Is it possible for me to tell F-spot with a special command or similar when I run it which db I want it so use? I.e. something like ```
f-spot --db=/home/sean/.gnome2/f-spot
``` and ```
f-spot --db=/home/shared/f-spot
```
so that I could have one desktop launcher that opens the family, shared, instance of F-spot, and another launcher to open my personal db. I would then be able to import the photos from the K7 into my personal collection first, then "drag 'n' drop" the ones I want to share into another F-spot window, and re-import them to the shared folder. I have lots of disk-space, so the double-up of disk usage doesn't bother me that much.

---

### Post by seanlano on 2009-08-30
Well, I figured it out. Just run: ```
f-spot -b /home/shared/f-spot
```. Turns out all I had to do was read the man page.

---

