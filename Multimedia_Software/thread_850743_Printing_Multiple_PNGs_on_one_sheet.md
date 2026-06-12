---
title: "Printing Multiple PNGs on one sheet"
date: 2008-07-05
forum: Multimedia Software
---

### Post by pdoconnell on 2008-07-05
I have a collection of several hundred 1 inch by 1 inch PNG files that I am trying to figure out how to print all at once. Specifically, I would like to print them adjacent to each other, creating row after row of them so I can easily cut them out. Is there a way to do this in any of the default-installed image viewers in Ubuntu 8.04, or even any software freely available that would do it?

---

### Post by kaibob on 2008-07-05
I don't know how to do what you want in a single step. You can do it in two steps by first creating a sheet with all of the individual PNG files. The montage command-line utility from the Imagemagick suite will do this.

A sample command that would apply to all PNG files in the current directory is:

```
montage *.png -geometry +2+2 output.png
```

After creating the montage sheet, you can print it with any graphics program. 

You can find more information on the montage utility at:

[http://www.imagemagick.org/script/montage.php](http://www.imagemagick.org/script/montage.php)

[http://www.imagemagick.org/Usage/montage/](http://www.imagemagick.org/Usage/montage/)

---

