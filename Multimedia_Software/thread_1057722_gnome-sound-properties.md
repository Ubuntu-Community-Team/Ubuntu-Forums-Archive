---
title: "gnome-sound-properties"
date: 2009-02-02
forum: Multimedia Software
---

### Post by Sandsound on 2009-02-02
Is there any way to access gnome-sound-properties from the terminal ?

Can't find a manual, (tried $man gnome-sound-properties) and I would like to toggle playing system sounds from the terminal.

EDIT. or maybe it is possible to find a config file for gnome-sound-properties ?

---

### Post by 73ckn797 on 2009-02-02
Maybe you can find some info at these links:

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[https://help.ubuntu.com/community/TitleIndex](https://help.ubuntu.com/community/TitleIndex)

---

### Post by Sandsound on 2009-02-02
> **73ckn797 said:**
> Maybe you can find some info at these links:

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[https://help.ubuntu.com/community/TitleIndex](https://help.ubuntu.com/community/TitleIndex)

Thanks... There's a lot if interesting info, but unfortunately I couldn't find the answer to my problem.

---

### Post by Sandsound on 2009-02-02
Found it :-)

$gconftool-2 -s -t bool /desktop/gnome/sound/event_sounds false

---

