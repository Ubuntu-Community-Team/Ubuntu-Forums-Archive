---
title: "ExifTool and EXIF modification using filename wildcards..."
date: 2015-07-19
forum: Multimedia Software
---

### Post by Z80A on 2015-07-19
Now, let's say I want to modify EXIF information in old files e.g. scanned photos using ExifTool to add camera make and model; -make and -model. These files are in some of the subfolders in my Pictures folder and I would recursively process these subfolders; -r.

But not all files are to be modified - only the ones with file names starting with cae1. cae1 may be followed by some 4-5 digit or characters. If I was only to modify a specific file, I would do it this way:

```
exiftool cae1-241a.jpg -make=CANON -model=AE-1 -P -overwrite_original
```

But to do it in all subfolders, I would add -r and somehow target the cae1 files, it would be neat to use some wildcard like cae1*:

```
exiftool cae1*.jpg -make=CANON -model=AE-1 -r -P -overwrite_original -progress -fast2
```

But ExifTool does not appear to support this (only extension filtering -ext) - any ideas?

---

### Post by PaulW2U on 2015-07-19
*Thread moved to **Multimedia Software**.*

Hi Z80A, please use code tags if you want to highlight input or output rather than use an alternative font.

if you are using New Reply button - highlight text and use the # button in the text box header. If you are using Quick Reply then add [noparse]```
 at the beginning of the section and 
```[/noparse] at the end.

---

