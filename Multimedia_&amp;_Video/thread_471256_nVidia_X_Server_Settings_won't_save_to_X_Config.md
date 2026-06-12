---
title: "nVidia X Server Settings won't save to X Config"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by stryker719 on 2007-06-11
I've got the nVidia drivers running beautifully on my computer, but I am unable to save my resolution change to the X Config file.  When I try to "Save to X Configuration File" the nVidia settings manager tells me that "Unable to remove old X config backup file 'etc/X11/xorg.conf.backup'"

Any thoughts on how I can correct this?  It's a pain having to reset my resolution each time I log in.

Thanks.

---

### Post by stryker719 on 2007-06-11
bumpity bump bump  :)

---

### Post by hiazle on 2007-06-11
Did you manually create the backup file? Or are you running the xconfig with root privileges?
One of these is a likely cause of your problem. You can try to rename the file "xorg.conf.backup" to something else e.g. "xorg.conf.old" and try updating your settings. 

Alternatively, you can try Alt+F2 then typing this command

```
sudo nvidia-settings
```

---

### Post by stryker719 on 2007-06-12
I wasn't running it as an admin so I couldn't make changes.  Thanks for the help!

---

### Post by mrbungle on 2007-06-30
thanks i have been trying to figure this out for a couple weeks now  ;)

why would it create a shortcut to nvidia in the menus but you can't save changes from that shortcut?

---

