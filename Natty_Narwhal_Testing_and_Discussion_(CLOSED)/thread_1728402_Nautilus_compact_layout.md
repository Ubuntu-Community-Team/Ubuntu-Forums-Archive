---
title: "Nautilus compact layout"
date: 2011-04-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by vaskark on 2011-04-13
In File Management preferences I usually choose 'Use compact layout'. This is working fine for everything except my home folder in Nautilus. I have another account on my system where it's working as it should. I tried deleting ~/.gconf/apps/nautilus from a console and logging back in, but it didn't help.

Any ideas?

---

### Post by Xgen on 2011-04-13
Have you tried right clicking on the folder pane -->arrange items --> compact layout?

---

### Post by vaskark on 2011-04-13
> **Xgen said:**
> Have you tried right clicking on the folder pane -->arrange items --> compact layout?

No I did not. But it works now :)
Many thanks.
So was it a bug? Since I didn't need to do this for my other account?

---

### Post by Xgen on 2011-04-13
Probably...never happened until I went from Lucid to Maverick, and then consistently with fresh installations. But, since I switched to a 24 " screen, I never use compact anymore except in specific folders -  e.g. usr/share/applications.

---

### Post by fjgaude on 2011-04-13
To get the compact arrangement in the home Nautilus I go to the menu View/Compact Arrangement, click it and it's done.

---

### Post by fjgaude on 2011-04-13
Here's a screenshot in the attachment.

---

### Post by mcduck on 2011-04-14
> **vaskark said:**
> No I did not. But it works now :)
Many thanks.
So was it a bug? Since I didn't need to do this for my other account?

Not really a bug, it's just that Nautilus can save the layout, background color and other view options separately for each directory, and if a directory has such settings they will override whatever the generic setting from Nautilus options is.

In other words, it had already saved the option for normal layout for your home directory, so that's what it used.

---

