---
title: "how to change xorg.config"
date: 2006-08-03
forum: Multimedia &amp; Video
---

### Post by potterpoole on 2006-08-03
how do you get pemision to change xorg.config manualy.

---

### Post by burquedout on 2006-08-03
U just sudo I believe, at least thats what i think it is, do you mean /etc/X11/xorg.conf?

---

### Post by TheGrinch on 2006-08-03
*potterpoole* - It's sudo gedit /etc/X11/xorg.conf
Then enter your password when prompted.

What I would like to know is how do I edit it from the text only mode/command line when ubuntu won't load the GUI? Being new to linux I made the mistake of using the ; to REM out some commands I had added instead of using the #. I soon found out ; is not a recognised command and causes Xserver to fail when loading. ](*,) 

Assistance would be greatly appreciated.

Cheers

---

### Post by burquedout on 2006-08-04
sudo nano /etc/X11/xorg.conf
thats the command that should let you edit it within the terminal :D

---

### Post by TheGrinch on 2006-08-04
> **burquedout said:**
> sudo nano /etc/X11/xorg.conf
thats the command that should let you edit it within the terminal :D

Thanks, I'll try that tonight.

---

### Post by potterpoole on 2006-08-04
Thanks to all for the info

---

