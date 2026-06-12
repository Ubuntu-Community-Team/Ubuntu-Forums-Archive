---
title: "Cannot chnage screen resolution"
date: 2008-01-14
forum: Multimedia &amp; Video
---

### Post by cigtoxdoc on 2008-01-14
I have two PCs running 7.10.  Cannot change screen resolution using Screen Resolution Preferences.  Is there a trick here as same PCs could change resolution running Debian?

John

---

### Post by Yellow Pasque on 2008-01-14
What video card(s) do you have and what do the /etc/X11/xorg.conf files look like?

---

### Post by wolfen69 on 2008-01-14
in terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

