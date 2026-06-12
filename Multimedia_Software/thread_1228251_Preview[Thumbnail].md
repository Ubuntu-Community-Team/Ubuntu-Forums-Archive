---
title: "Preview[Thumbnail]"
date: 2009-07-31
forum: Multimedia Software
---

### Post by Hoom@n on 2009-07-31
How can I have a thumbnail view of more files in Nautilus? e.g. I have preview of .ogv files, but I don't have preview of .avi files.

---

### Post by starcraft.man on 2009-07-31
> **Hoom@n said:**
> How can I have a thumbnail view of more files in Nautilus? e.g. I have preview of .ogv files, but I don't have preview of .avi files.

You need the right video codecs to get thumbnails for all video files. Installing the package ubuntu-restricted-extras will fix it, big package but has lots of useful programs I won't go into. Make sure you have the restricted packages in software sources enabled. See my sig for details on installation.

---

### Post by vinutux on 2009-07-31
Sudo apt-get install ubuntu-restricted-extras

---

### Post by Hoom@n on 2009-08-02
I had the codecs to play that file(I installed what Totem suggested me at first attempt to play) when I took the screenshot.
I installed "ubuntu-restricted-extras" and nothing changed!
+that .avi is a DivX movie.
+I like to have more previews like for .odp files!

---

### Post by vinutux on 2009-08-02
> **Hoom@n said:**
> I had the codecs to play that file(I installed what Totem suggested me at first attempt to play) when I took the screenshot.
I installed "ubuntu-restricted-extras" and nothing changed!
+that .avi is a DivX movie.
+I like to have more previews like for .odp files!

if you really want that ```
rm /home/[COLOR="Red"]yourusername[/COLOR]/.thumbnails/
```

---

### Post by Hoom@n on 2009-08-03
> **vinutux said:**
> if you really want that ```
rm /home/[COLOR="Red"]yourusername[/COLOR]/.thumbnails/
```
Sorry, what's that?

---

### Post by vinutux on 2009-08-03
> **Hoom@n said:**
> Sorry, what's that?

removing yout thumbnail cache...so its reladed..[works fine for corrupted cache]

---

### Post by Hoom@n on 2009-08-10
Please look at the attached picture, there is a preview for some files and there is not for one. (the file with no preview is the file mentioned in first post and other files are added after installing ubuntu-restricted-extras.[even before installing that package I was able to play that file] should I do what is said in post #5? is it safe?)

---

