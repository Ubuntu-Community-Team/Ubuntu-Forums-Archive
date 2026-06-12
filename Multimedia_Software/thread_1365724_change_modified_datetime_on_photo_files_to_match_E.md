---
title: "change modified date/time on photo files to match EXIF data?"
date: 2009-12-27
forum: Multimedia Software
---

### Post by activematrix on 2009-12-27
Hi, 
I am looking for some help creating a script to read exif data from photos and change the created or modified date/time to match said exif data.  This script would have to be able to be given a folder, and it would go through all subfolders, and it would have to be able to handle multiple file types.  I have exiftool installed, if that helps.

Thanks a million!
Chris

---

### Post by amac777 on 2009-12-27
Here is a script I use for something smilar. It only updates the .JPG's in the current directory, which is all I needed it to do. You may be able to modify it for your purposes.

```
#!/bin/bash

for f in *.JPG;
do
  x=`exiftool -d '%c' -DateTimeOriginal $f`;
  touch -d "`echo $x | sed 's/Date\/Time\ Original\ :\ //'`" $f;
  echo $f;
done

```

---

### Post by wilbertvolkers on 2012-01-09
Another possibility:

[COLOR=#c20cb9]** sudo**[/COLOR] apt-get [COLOR=#c20cb9]**install**[/COLOR] jhead
jhead -ft *.jpg

---

### Post by coffeecat on 2012-01-09
Old thread. Closed.

---

