---
title: "Change an image file's extension to be correct"
date: 2011-10-31
forum: Multimedia Software
---

### Post by marblecatdog on 2011-10-31
So I have a bunch of image files, most of which are .png files, but when I try to view them, the ubuntu image viewer can't display them because it says the files are not png files.  However, if I simply change the file extension from picture.png to pictue.jpg, it works fine (so far I haven't found any that are .jpg that need to be changed to .png).  I have a bunch of pictures with this problem, is there any program or method that I could use to fix all of the images file extensions, I can't just rename the extension with a bulk renamer either because I have plenty of working image files in that folder, and sorting them all out doesn't really save me any time.

---

### Post by papibe on 2011-10-31
Hi marblecatdog.

It can be done. All you need is to write a little bash script. These are the key tricks:

You can use the command 'file' to determine the real content of the picture. For example:
```
$ file picture.png 
picture.png: PNG image data, 1366 x 768, 8-bit/color RGB, non-interlaced

$ mv picture.png picture.jpg
$ file picture.jpg 
picture.jpg: PNG image data, 1366 x 768, 8-bit/color RGB, non-interlaced

$ mv picture.jpg picture.xxx
$ file picture.xxx 
picture.xxx: PNG image data, 1366 x 768, 8-bit/color RGB, non-interlaced

```
As you can see 'file' would recognize a PNG file regardless of a bad extension.

Tell us if you need more help with that.
Regards.

---

### Post by marblecatdog on 2011-11-01
Thanks, but I actually got bored and wrote a little java program to do the work for me, I'm not very familiar with bash stuff but thanks for the help if anyone else has this problem!

---

