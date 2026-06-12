---
title: "dual moniter on reboot...."
date: 2010-12-14
forum: Multimedia Software
---

### Post by adduds on 2010-12-14
Hey I've got dual monitors on my ubuntu 10.10 with nvidia geforce 7600GT.

Problem is I'll configure them to work between each other then whenever i reboot the one monitor doesn't work and i have to reconfigure.....

any ideas on how to make my monitor preferences stick?

cheers

---

### Post by adduds on 2010-12-15
bump


Not clear or no ideas?

---

### Post by tjones00 on 2010-12-15
Try running "NVIDIA X Server Settings" from a terminal as root.

Open a terminal and type.

```
sudo nvidia-settings
```

Setup your monitors like usual under "X Server Display Configuration" and "Save to X Configuration File"

This should pretty much guarantee that your xorg.conf gets saved. If it still gives you errors at "Save to X Configuration File" select the option "Show preview" and copy/paste the information into your /etc/X11/xorg.conf manually.

---

