---
title: "Application for cataloging photos on DVDs?"
date: 2012-03-27
forum: Multimedia Software
---

### Post by zzarko on 2012-03-27
I have about 20 DVDs with misc photos/images, and I need an application that could scan those DVDs, make thumbnails of photos, so that I can browse those thumbnails without inserting the DVD. I DO NOT want to import all those photos/images to HD, I just need a way to quickly find something, and then to insert appropriate DVD if I want the actual photo/image.

I have tried numerous collection managers, photo managers and disk catalogues, but none of them have what I'm looking for (or, I was unable to find such an option). DigiKam is the closest I got (it can make thumbnails of photos from removable media), but in order to view thumbnails, I need to insert the DVD, which is kind of useless to me.

Anyway, does anyone know any Linux software that can make thumbnails of photos from DVDs, remember the file structure on DVDs, and display those thumbnails without inserting DVDs?

I know I can probably make a script that generates thumbnails on HD, with exact file structure as on DVD, but I'm looking for database-like soultion (to avoid thousands of small files).

Best regards,
Zarko

---

### Post by zzarko on 2012-03-28
After successfully finding nothing that can do what I need, I made a Python script to do the task. The script can be found at:

[http://www.acs.uns.ac.rs/sr/filebrowser/download/764](http://www.acs.uns.ac.rs/sr/filebrowser/download/764)

It has a few command line options (see help) and requires Python 2.7 and ImageMagick.
Example usage: if you put disc named "Travels 01" in your DVD drive and run the script as```
./thumbcat.py /media/Travels\ 01/
```you'll get thumbnails in "~/PhotoCollection/Travels 01/" (it is presumed that disc will be mounted with that name in /media directory).

Still, if anyone knows any other solution, please tell.

Best regards,
Zarko

---

### Post by MadHatter93 on 2012-03-30
Shotwell has an "Import in place" setting that will allow you to add photos to the database, but not actually copy them to the library file. Does that not work?

---

### Post by zzarko on 2012-04-02
> **MadHatter93 said:**
> Shotwell has an "Import in place" setting that will allow you to add photos to the database, but not actually copy them to the library file. Does that not work?First, thanks for answering me! In my Shotwell (0.11.6) I didn't found such an option. Do you use newer version?

I did try Shotwell in my quest for cataloging, but I was unable to find simple way to see full path to image (I need that, because my DVDs have images sorted in directories). Also, if I find a version that have "Import in place", wouldn't Shotwell delete images that no longer exist (the ones that are on removable media)?

---

### Post by zzarko on 2012-04-02
OK, I found out that if I hold Ctrl+Shift while dragging pictures from Nautilus, they will just be added to Shotwell without copying. But, as soon as I remove DVD with images, they are gone from Shotwell also. So, unfortunately, this program won't help me...

---

