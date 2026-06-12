---
title: "JPG Thumbnail Recursive app help..."
date: 2014-07-25
forum: Multimedia Software
---

### Post by david-oldcolo on 2014-07-25
I have several tens of thousands of .jpg files that I need to create thumbnails.  I've been poking around for any app or script that can do this, and also with a consideration for speed tho finding something that will create thumbs and recurse down many subdirs is key.

Have found various scripts for a single directory only, and there are apps that can do a 'single directory' as well.  But can anyone point to a script that creates thumbs from 2-5MB sized .jpgs, many, and recurse directories as well?

---

### Post by david-oldcolo on 2014-07-27
No ideas?

---

### Post by vanadium on 2014-07-27
You already have several thumbnail generation utilities installed:
```

apropos thumbnail

```

---

### Post by david-oldcolo on 2014-07-28
Tx.  I studied this but here was the output from running it...

apropos thumbnail 
evince-thumbnailer (1) - create png thumbnails from PostScript and PDF documents
shotwell-video-thumbnailer (1) - writes video thumbnail to stdout
thumbnail (1)        - create a TIFF file with thumbnail images
totem-video-thumbnailer (1) - video thumbnailer for the GNOME desktop
xvminitoppm (1)      - convert a XV "thumbnail" picture to PPM
SDIM0395.jpg: nothing appropriate.
SDIM0398.jpg: nothing appropriate.
SDIM0399.jpg: nothing appropriate.
SDIM0400.jpg: nothing appropriate.
SDIM0401.jpg: nothing appropriate.

And I worked to study more usage of the command line.  I was not able to figure out how to use this command, but thanks anyway.  I will continue looking for a function that will create thumbnails recursively through directories.  tx




> **vanadium said:**
> You already have several thumbnail generation utilities installed:
```

apropos thumbnail

```

---

### Post by vanadium on 2014-07-28
totem-video-thumbnailer is the command used by nautilus to generate its thumbnails. With the command "man totem-video-thumbnailer" you can see the help page for the utility, and how you can use it yourself on the command line. In its simplest form, usage is
```

totem-video-thumbnailer <infile> <thumbnail>

```

To work recursively across subdirectories, you can use find with the -exec option:
(disclaimer: I did not test any of these)
```

find <starting_directory> -iname='*.jpg' -exec totem-video-thumbnailer -j "{}" "{}"thmb\.jpg \;

```
That would output thumbnails named like "picture.jpgthmb.jpg" next to each corresponding graphic.

---

