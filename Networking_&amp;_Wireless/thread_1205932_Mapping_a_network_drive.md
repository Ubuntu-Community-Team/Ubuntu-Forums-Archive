---
title: "Mapping a network drive"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by fluidbyte on 2009-07-06
Relatively new to *nix, and I've been working on mounting network shares on my Windows network.  I wrote a script that seems to work:
```

#!/bin/bash
sudo /sbin/mount.cifs //myserver/share /media/share

```I am having two issues (perhaps 1 will fix the other):

1.  When I run the script it brings up the terminal and requires me to enter my password.
2.  I can't get it to run on startup (yes - I tried System >> Preferences >> Startup Applications, and linking to the script).

Any help would be greatly appreciated.

Also - is there a way I could add multiple shares to this?  I tried adding another line and it didn't seem to work... may be my lack of scripting experience.

---

### Post by Boondoklife on 2009-07-06
It is going to ask you for your password as it needs one to provide to the other machine. You might want to look into either adding the mappings to your fstab file or using gvfs in a startup script.

the later will require you to connect to the share once and input your password and then click the remember password option.

---

### Post by michaelzap on 2009-07-06
I recommend that you use GVFS to mount your share, as explained here:
[http://ubuntuforums.org/showthread.php?p=7572972](http://ubuntuforums.org/showthread.php?p=7572972)

The [fstab method]("http://www.ubuntuforums.org/showthread.php?t=288534") works as well (you basically just add your mount paths and options to /etc/fstab), but there is a pesky bug dismounting shares on shutdown that makes this method problematic.

---

