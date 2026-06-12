---
title: "Disabling CD-ROM mount on client pc's ?"
date: 2005-12-25
forum: Networking &amp; Wireless
---

### Post by tuxy on 2005-12-25
Sorry to repeat the post in Gnome Support and in Networking :confused: 

I have a thin client setup running at my home network using Ubuntu Breezy. What's happening is if I mount the CD-ROM on one user and run the cd, there is a window popping up on all the thin clients in the network and displaying the contents of the CD. I don't want this to happen. Is there any way that I can disable this option?

I got 2 more queries:

1) How to make the desktop background image common to all the users?
2) I don't want the /home directories of one user to be viewed other users. I know that we can do that through 'chmod' and 'chown'. Is there any other way using the Gnome tools ?

Cheers.

---

### Post by geearf on 2005-12-26
2-  try to right click on the folder in nautilus; and change its properties.

---

### Post by tuxy on 2005-12-26
Thank you mate :)

---

### Post by kaamos on 2005-12-26
1)
- Set a wallpaper on one user
- From that users home directory, copy this file to the same directory on other users home directories.
> /home/**username**/.gconf/desktop/gnome/background/%gconf.xml
Note: this has not been tested, but this looks like where gnome keeps the wallpaper setting. And if you don't want the other users to be able to change that, just remove the write permission..

---

