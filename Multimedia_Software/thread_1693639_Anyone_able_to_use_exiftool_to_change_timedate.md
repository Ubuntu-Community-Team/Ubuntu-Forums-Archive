---
title: "Anyone able to use exiftool to change time/date?"
date: 2011-02-23
forum: Multimedia Software
---

### Post by mmcmonster on 2011-02-23
Hi.
  I'm trying to change the time stamps on a bunch of pictures in the same directory, because several cameras were used, some of them with the wrong time zone.
  exiftool seems to be the correct package to use, but it doesn't seem to work.

The following command seems to be the recommended way to subtract 1 hour from all .JPG files in the directory, but the exif data in the file and even the time stamps don't change. :-(
```
exiftool -a -AllDates -=01:00 .
```Any thoughts on what I'm doing wrong?

---

### Post by An Sanct on 2011-02-23
What is the error message? I don't know exiftool, but maybe you have to use sudo...

---

### Post by boardhead on 2011-02-24
There should be no space before the "-=".  Also, the -a option is superfluous.  Try this:

```
exiftool -alldates-=1 .
```

Here, "1" has the same effect as "1:00", but is faster to type. :)

- Phil

---

