---
title: "how to change date tag on pics"
date: 2011-12-12
forum: Multimedia Software
---

### Post by Kaizoku001 on 2011-12-12
I just scanned a bunch of pages from  a book i have and would like to import the jpeg to my iPad. Unfortunately, iPad uses some demented system to order the pics in an unfathomable chronological order. 

Is there any good batch converting software that can help me batch edit the created date tag on all my pics?
Thanks

---

### Post by tjoff on 2011-12-12
If the date tag you are referring to is [EXIF]("http://en.wikipedia.org/wiki/Exchangeable_image_file_format") data, you should have a look at jhead.

---

### Post by Kaizoku001 on 2011-12-12
> **tjoff said:**
> If the date tag you are referring to is [EXIF]("http://en.wikipedia.org/wiki/Exchangeable_image_file_format") data, you should have a look at jhead.
seems like it can do what I need...
But the command line looks like hell. I'm not too good with that sort of things.

---

### Post by Lampi on 2011-12-12
phatch does offer a gui to handle metadata, but it's aimed at batch processing.

---

### Post by sreilly on 2011-12-12
jhead  -n%y%m%d-%H%M%S *jpg

Will rename all your jpg files to the date/time they were created.

Steve

---

