---
title: "different skins in BMP????"
date: 2007-04-05
forum: Multimedia &amp; Video
---

### Post by lanchongzi on 2007-04-05
hi guys

i just downloaded a whole bunch of winamp skins to use with BMP
problem is that i cant copt them in the bmp skin folder.
it is read only

how can i manage this 
( using the terminal???  dont really know how to do this :(  )


every help is appreciated


:)

---

### Post by mssever on 2007-04-05
You probably need root access to do this. Hit Alt+F2 to bring up the run dialog, then type ```
gksudo nautilus
``` This will give you a file browser window with root priviledges. I suggest that you go to Edit > Backgrounds and set a hideous background color to remind you never to use a root nautilus unless you have to.

---

### Post by reclusivemonkey on 2007-04-05
> **lanchongzi said:**
> hi guys

i just downloaded a whole bunch of winamp skins to use with BMP
problem is that i cant copt them in the bmp skin folder.
it is read only

how can i manage this 
( using the terminal???  dont really know how to do this :(  )


every help is appreciated


:)

As the poster above says, the main bmp themes folder will be owned by root. However, you will probably find a bmp config folder in your home directory, and you should be able in install the themes there. Have a look for ~/.bmp.

---

### Post by lanchongzi on 2007-04-07
thanks mssever  the command worked

i just found it as well in a different thread  :)

so, the  gksudo nautilus  command shoulod work for all folder that are assigned too root, right?

---

### Post by mssever on 2007-04-08
> **lanchongzi said:**
> so, the  gksudo nautilus  command shoulod work for all folder that are assigned too root, right?
That's correct.

---

