---
title: "Xsane help"
date: 2009-04-12
forum: Multimedia Software
---

### Post by delboy1 on 2009-04-12
Can anyone help me get from this view
[http://www.xsane.org/doc/xsane-color-correction.jpg]("http://www.xsane.org/doc/xsane-color-correction.jpg") to this view in xsane [http://www.xsane.org/doc/xsane-viewer.jpg]("http://www.xsane.org/doc/xsane-viewer.jpg")

I have a Dell mini 9 and am stuck in the first screen on which I can't see the bottom (or find any way to resize it or move to the bottom) thus I can't click on the scan button which makes the whole program useless.

---

### Post by drs305 on 2009-04-12
I have the display you are trying to obtain but was not able to recreate what you currently have. One thing you could do is to rename your ~/.sane folder, which contains your xsane folder and settings. After renaming it, open xsane again and it will recreate the folder. You would have to re-input your directory and personal information, but you may get the 'more-or-less' default menu you are looking for.

```

mv ~/.sane ~/.sanex && xsane

```

If it doesn't solve things, delete the new .sane folder and restore the old one.

---

