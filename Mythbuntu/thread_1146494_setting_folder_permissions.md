---
title: "setting folder permissions?"
date: 2009-05-02
forum: Mythbuntu
---

### Post by Arminius on 2009-05-02
I right click on a folder, and all the permission options are greyed out, I log on in terminal as root, but still no permission options.

so how would I go about setting it so when u try to enter a folder u have to enter the admin password?

---

### Post by jb5 on 2009-05-03
I'm not entirely sure I completely understand your question, but if you want to run a GUI file browser as root try running:-```
sudo nautilus
```or```

sudo thunar
``` (depending on which file browser you have installed).
Whether this is entirely the safest way to do what you want is another matter!

You might want to check out chmod & chown for command line tools to do this.```
man chown
man chmod
```

HTH

---

### Post by AlecJ on 2009-05-03
> **Arminius said:**
> I right click on a folder, and all the permission options are greyed out, I log on in terminal as root, but still no permission options.

so how would I go about setting it so when u try to enter a folder u have to enter the admin password?


You want to password lock a folder?
Try here
[http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/](http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/)

---

