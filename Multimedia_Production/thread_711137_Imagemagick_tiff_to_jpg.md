---
title: "Imagemagick: tiff to jpg"
date: 2008-02-29
forum: Multimedia Production
---

### Post by Wardazo on 2008-02-29
Hi

I'm trying to batch covert with perlmagick, but I don't even seem to be able to manage it on the command line!!

```
 mogrify -format jpg -quality 70 -resize 300x300 file.tif
```

When I do this sure enough the image converts to jpg, shrinks to 300 by 300 but it's over one megabite in size on the disk; however, it's current memory size is about 50kb when I open it. 

What am I doing wrong?

It Ubuntu 6.06 server edition

Ward

---

### Post by Creative2 on 2008-02-29
mm i know this 

convert  -resize 800x600 -quality value  INPUT.any  OUTPUT,jpeg

---

### Post by Wardazo on 2008-02-29
Yes that should work, but with a 30mb .tif file I get a almost a 2mb jpg file using that command.

It's a different problem, I think related to large tif files... but I'm not really sure.

Thanks though.

Any other suggestions?

---

### Post by Wardazo on 2008-02-29
SOLUTION: use the -strip flag

Just in case anyone has the same problem.

---

### Post by stani on 2008-02-29
You can also use Phatch for this:
[http://photobatch.stani.be](http://photobatch.stani.be)

[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598)

---

