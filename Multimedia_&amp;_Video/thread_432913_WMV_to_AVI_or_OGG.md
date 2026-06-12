---
title: "WMV to AVI or OGG"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by tompot on 2007-05-04
Does anyone know good application (with graphical GUI) which can be used to convert wmv files to any other formats (e.g. ogg, avi)?

---

### Post by disturbed1 on 2007-05-04
Avidemux will edit/encode non-drm wmv files.

---

### Post by jfinkels on 2007-05-04
If you don't mind the command line, you can use the program "mencoder", which encodes and decodes movie files very quickly and easily.
```

sudo aptitude install mencoder

```

---

### Post by Andy on 2008-04-10
mencoder movie.wmv -o movie.avi -ovc lavc -oac lavc


more info here : [http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide#The_Basics](http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide#The_Basics)

---

