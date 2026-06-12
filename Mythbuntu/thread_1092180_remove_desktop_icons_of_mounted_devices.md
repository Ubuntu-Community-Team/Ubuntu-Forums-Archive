---
title: "remove desktop icons of mounted devices"
date: 2009-03-10
forum: Mythbuntu
---

### Post by nikolaibelkin on 2009-03-10
Hi I wanted to have absolutely no desktop icons visible. I deleted all desktop icons, but when I insert a CD or plug in a USB an icon is displayed on the desktop, is there anyway to hide these icons?

---

### Post by nikolaibelkin on 2009-03-15
Nevermind, I found the fix. Firstly I typed sudo locate xfdesktop and found that a README file existed in /usr/share/doc/xfdesktop4-data/. In that file it says that to get rid of these icons you should modify the file ~/.config/xfce4/desktop/xfdesktoprc or create it if it doesn't exist. The file should look like:

```
[file-icons]
show-filesystem=true
show-home=true
show-trash=true
show-removable=true
```

then just change the ones you want to false.

---

