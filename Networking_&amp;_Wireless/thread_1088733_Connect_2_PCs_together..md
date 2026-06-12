---
title: "Connect 2 PCs together."
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by Surreal Killa on 2009-03-06
I have 2 PCs sitting next to each other, both running Xubuntu, both connected to the internet through the same router, and the internet works on both PCs. But I'm wondering how I could connect from one to the other? Sorry if this is a noob question, I have little experience with setting up networks.

---

### Post by pytheas22 on 2009-03-06
There are lots of ways to do this.  Which one you choose should depend on what your goal is.

If you want to share files between the two machines, install samba (you will be automatically prompted to do this if you right-click on any folder on Ubuntu, select 'Sharing Options' and enable the folder to be shared).

If you want to be able to connect via the command line between the two machines, install an ssh server on each one by typing:
```

sudo apt-get install ssh
```

Then you can connect from one to the other by opening a terminal and typing:

```
ssh username@IP-address
```

for the machine you want to connect to.  You can also use ssh to share files.

If you want to control the graphical desktop of the machines, go to System>Preferences>Remote Desktop and enable desktop sharing.  Then use the client at Applications>Internet>Remote Desktop Viewer to connect from one machine to the other.

EDIT: sorry, I reread your post and see that you're using Xubuntu, not Gnome.  Some of these instructions are Gnome-specific, but you should be able to find the Xubuntu equivalents relatively easily, I think.

---

### Post by Surreal Killa on 2009-03-06
Thanks, I will try that.

EDIT:

This is awesome! It works. :)

---

