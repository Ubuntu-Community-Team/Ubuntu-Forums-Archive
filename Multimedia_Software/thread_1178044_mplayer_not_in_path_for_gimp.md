---
title: "mplayer not in path for gimp"
date: 2009-06-04
forum: Multimedia Software
---

### Post by kolibri on 2009-06-04
I'm trying to run the Mplayer based extraction (split video into frames- Gimp Gap) in Gimp.  

Gimp 2.6.1
Mplayer 2.1

Mplayer is installe, and in my video menu.  However, when i try to run the extraction in gimp I get the following error message:

If your mplayer is not in  your PATH or is not named mplayer you have to set environment variable GAP_MPLAYER_PROG to your mplayer program and restart gimp.

I'm pretty sure it's named mplayer  (MPlayer?), so you do I set the environmental variable it specifies?

I love Ubuntu, but I'm not that far into linux to be able to figure out the system stuff like that.

TIA-

---

### Post by Lampi on 2009-06-04
try this: "which mplayer"

this shows you the path to your mplayer binary - mine is "/usr/bin/mplayer"

now you export this path into your environment - type in console:

"export GAP_MPLAYER_PROG=/usr/bin/mplayer"

now you restart gimp

---

### Post by ad_267 on 2009-06-04
If you type "export GAP_MPLAYER_PROG=/usr/bin/mplayer" in a terminal you'd have to start gimp from the same terminal with "gimp".

For that setting to be applied permanently you'd have to edit the ~/.bashrc file and add that line.

---

### Post by Lampi on 2009-06-04
true! exports like this are only temporary - if it fixed the problem it's okay to place the export into ~/.bashrc

---

