---
title: "Template Mythbuntu - Project Grayhem"
date: 2008-12-26
forum: Mythbuntu
---

### Post by erhapp on 2008-12-26
There seems to be a problem with the Mythbuntu / Project Grayhem template in both 8.04 and 8.10 versions of Mythbuntu.

Both templates display to many (2) items when showing pictures/folders in the image-viewer.

Each row contains 2 items that can not be shown on screen. So when using the right arrow. The selector disappears from the screen (right hand side) for two keypresses before reappearing over the first picture on the next line.

What is the best way to resolve this problem and force the template to show less images (thumbnails) on each line?

---

### Post by joho500 on 2008-12-26
I have the same problem.

Joost

---

### Post by erhapp on 2008-12-28
Is there anybody who can help both of us?

I would love to get this template up and running.

Because of this error the current template is quite unusable.

It would be great to have a fixed version in the next Mythbuntu release.

---

### Post by EasyRiderOnTheStorm on 2008-12-28
That's strange. Project Grayhem works mostly OK for me (4 images in a row, all visible). How many do you have? What's your frontend screen resolution? Are you using a "wide" version of the theme perhaps...?

---

### Post by SiHa on 2008-12-28
Have you tried the non-widescreen version? For me, only the widescreen version exhibits this behaviour.

---

### Post by erhapp on 2008-12-31
I've this problem with both widescreen and normal versions.

---

### Post by erhapp on 2008-12-31
> **EasyRiderOnTheStorm said:**
> That's strange. Project Grayhem works mostly OK for me (4 images in a row, all visible). How many do you have? What's your frontend screen resolution? Are you using a "wide" version of the theme perhaps...?

I'm indeed using the wide version on a 1080p LCD TV. (using native TV resolution).

I'm getting 6 images in a row.

---

### Post by joho500 on 2008-12-31
Hi all,

Because no solution was given I searched the internet and I've adjusted the theme-file myself. I've attached the updated file (gallery-ui.xml.txt). Rename it to gallery-ui.xml and  sudo copy it into /usr/share/mythtv/themes/ProjectGrayhem-wide. You might want to backup the current version first.

It works on my setup. Hope it works on yours too, erhapp. 

Cheers,
Joost

---

### Post by erhapp on 2009-01-04
Thanks

This solved my problem.

Let's hope that someone is kind enough to upload your version of this file to de Mythbuntu dev-tree. This way the template will just work in the next release of mythbuntu.

> **joho500 said:**
> Hi all,

Because no solution was given I searched the internet and I've adjusted the theme-file myself. I've attached the updated file (gallery-ui.xml.txt). Rename it to gallery-ui.xml and  sudo copy it into /usr/share/mythtv/themes/ProjectGrayhem-wide. You might want to backup the current version first.

It works on my setup. Hope it works on yours too, erhapp. 

Cheers,
Joost

---

