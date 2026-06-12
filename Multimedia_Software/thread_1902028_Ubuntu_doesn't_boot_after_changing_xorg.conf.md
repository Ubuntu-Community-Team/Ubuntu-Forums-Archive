---
title: "Ubuntu doesn't boot after changing xorg.conf"
date: 2011-12-29
forum: Multimedia Software
---

### Post by TomAwezome on 2011-12-29
It's really about as simple as the title. Ubuntu simply just doesn't boot.

Using recovery mode I can get to the root shell, which I can't really use as it's read-only.
If I try to use "remount", even after 20 minutes, it just hangs with this:
```
fsck from util-linux 2.19.1
/dev/sda5: clean, 450828/9641984 files, 7288848/38549504 blocks (check after next mount)
[  219.409973] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
```
Selection the "fsck" option just hangs with ```
fsck from util-linux 2.19.1
```
Another thing I've noticed is that, when using Ctrl-C to exit them, even Ctrl-C gets stuck on ```
* Checking battery state...
``` (even though I use a desktop computer)

---

### Post by TomAwezome on 2011-12-29
Phew! Nevermind, I managed to fix this. After a painstaking 1-2 hours I managed to find a good solution.

First I dropped into the root shell.
Then I typed in ```
mount -rw -o remount /sda5
```
Then, using ```
nano
``` I put these to their defaults:
[LIST]
[*]/etc/lightdm/lightdm.conf
[*]/etc/lightdm/unity-greeter.conf
[*]/etc/X11/xorg.conf (you can delete this one or just clear it out, whichever suits you)
[*]/etc/gdm/Init/Default
[/LIST]
After that it worked fine!
Hooray for learning myself? :D

---

