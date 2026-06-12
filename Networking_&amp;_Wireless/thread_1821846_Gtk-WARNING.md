---
title: "Gtk-WARNING"
date: 2011-08-09
forum: Networking &amp; Wireless
---

### Post by nego0 on 2011-08-09
Im trying to get my wireless pci card to work 
and had help with this _[Thread](http://ubuntuforums.org/showthread.php?t=1780136)_
But it seems i got some other issues preventing me from doing so

every time i want to black list something like this:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```

and try to save the file the terminal shows me this:
```
desmania@desmania-MS-7100:~$ gksu gedit /etc/modprobe.d/blacklist.conf

(gedit:3601): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3601): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.TL23ZV': No such file or directory

(gedit:3601): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3601): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.47H2ZV': No such file or directory

(gedit:3601): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```

really need some help here!

Thnx

---

### Post by nego0 on 2011-08-09
Is it because gksu gedit cannot get access to Root or something like that so it automatically says is doesn't exist???
or the file is stored somewhere else???

---

### Post by Derek Karpinski on 2011-08-09
The directory doesn't exist.
 
Easy fix:
 
```
sudo mkdir /root/.local/share
```

---

### Post by deceaseddolphin on 2011-09-21
Thank you!

It worked.

---

