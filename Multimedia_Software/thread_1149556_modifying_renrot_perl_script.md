---
title: "modifying renrot perl script"
date: 2009-05-05
forum: Multimedia Software
---

### Post by GabrielWolff on 2009-05-05
I am trying to get renrot to put my renamed files into specified folders. 
I'd like it to result in the following structure:
```
YYmmdd/YYmmddhhmmss.jpg
``` I was looking at the perl script and I found the place I thought I have to play around with, but I couldn't convince renrot to change the file names to the above mentioned name, including a division into different directories. The result I got was ```
gabriel@gabriel-laptop:~/Desktop/100_FUJI$ renrot *JPG
RENAMING / ROTATING
===================
Processing file: (1 of 122) 080517224447.JPG ...
FATAL: Unable to rename 080517224447.JPG -> 0805/080517224447.JPG.
Died at /usr/bin/renrot line 786.
```
How can it be done?

---

