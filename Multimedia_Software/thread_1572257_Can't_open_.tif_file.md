---
title: "Can't open .tif file"
date: 2010-09-10
forum: Multimedia Software
---

### Post by locosway on 2010-09-10
When I try to open a .tif file that I created using:

```
pfsin pfs.hdr | pfstmo_mantiuk06 -e 1 -s 1 | pfsgamma --gamma 2.2 | pfsout pfstmo_mantiuk06.tif
```

I get an error in gimp and eye of gnome:

```
**TIFF image Message**
Failed to allocate memory for to read TIFF directory (0 elements of 12 bytes each)

**TIFF image Message**
/home/greg/Downloads/hdr/pfstmo_mantiuk06.tif: Failed to read directory at offset 0

**GIMP Message**
Opening '/home/greg/Downloads/hdr/pfstmo_mantiuk06.tif' failed:

TIFF image plug-In could not open image
```

The two images I created are the same size. Not sure if this is a coincidence, or an indicator of an error.

Any help would be appreciated.

---

