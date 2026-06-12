---
title: "exif reports Corrupt data"
date: 2018-11-28
forum: Multimedia Software
---

### Post by bill-lancaster on 2018-11-28
I've scanned a large number of old photos to jpg files and then attached descriptive tags to them.
As a routine I convert the file to an exif compatible format:-
```
exif --create-exif /home/bill/Documents/Genealogy/Photos/GPR0125.jpg
```
but some files produces this error:-
```
Corrupt data
The data provided does not follow the specification.
jpeg-data: Data does not follow JPEG specification.

```
What can I do to correct this?

---

### Post by bill-lancaster on 2018-11-30
Solved!  Many of the scanned files were in fact .pnm despite having a .jpg extension!

---

