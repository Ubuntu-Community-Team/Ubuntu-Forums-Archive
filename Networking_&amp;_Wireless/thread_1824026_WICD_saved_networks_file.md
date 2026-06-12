---
title: "WICD saved networks file"
date: 2011-08-13
forum: Networking &amp; Wireless
---

### Post by Lockheed on 2011-08-13
Can someone tell me what is the location of the file in which WICD stores information about wifi networks (i,e, names and passwords)?

I need to change permissions on the file because it won't save new networks.

---

### Post by thefasterblueone on 2011-08-13
```
/etc/wicd/wireless-settings.conf
```

---

### Post by Lockheed on 2011-08-13
This file is empty even though I have several networks saved.

---

### Post by thefasterblueone on 2011-08-13
Check in:

```
/var/lib/wicd/configurations/
```

---

### Post by Lockheed on 2011-08-13
The only file with content there says this:
> If you're reading this file, that means that you found a directory that
is empty by default when Wicd is installed. Congratulations!

At this point, the directory probably isn't empty, so perhaps the name
of this file is a little confusing.

Some package managers and some version control systems don't allow for
installation or storage of empty directories, so this file exists to
make them work properly. Just ignore it and continue on with your life.


---

