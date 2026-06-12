---
title: "Vector fonts (*.vbf) can't be seen"
date: 2009-10-16
forum: Multimedia Software
---

### Post by gradysghost on 2009-10-16
I found a website with a ton of great open source fonts.  I've downloaded a handful of them because they're really quite nice and I'd like to use them.

Problem is, no matter what I try, none of those fonts in *.vbf (vector-based font) format will load in any software.

I put the files into /usr/share/fonts/truetype/opentype/* where each has its own directory, logged out, and logged back in.  This made some fonts work (the *.otf fonts that I used), but **all** *.vbf fonts did not load.

I rebuilt my font cache:

```
sudo fc-cache -f -v
```

This produced no errors, and actually ends with "succeeded".  I've attached that output to this post (fc-cache-output.txt).

I also printed out a list of available fonts:

```
fc-list
```

I've attached that as well (fonts.txt).  Google so far has been no help at all.  I hope someone here can tell me how to enable support for vector-based fonts in Ubuntu.

Thanks in advance!

---

### Post by gradysghost on 2009-10-16
I'm installing a package right now (technically a metapackage) called lcdf-typetools.  I'm hopeful.  I'll update with results when I'm done.

---

### Post by gradysghost on 2009-10-16
FWIW, I don't think these are vector fonts as the file extension originally made me think.  I now believe they are Multiple Master fonts, which appear to be a Mac/Adobe kind of thing.

---

### Post by gradysghost on 2009-10-16
That didn't seem to install any kind of inherent ability to view these files.  Apparently, that package contains various programs to convert the files, but I can't make it work.  Nothing seems to be able to comprehend these files.  Google searches are basically worthless on this (going to foreign sites at about the fifth hit or so).

So I guess I'm looking for a fonts expert to help me work this out.  I'm not buying a Mac on account of some pretty fonts.

---

