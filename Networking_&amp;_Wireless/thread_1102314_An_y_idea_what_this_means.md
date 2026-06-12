---
title: "An y idea what this means?"
date: 2009-03-21
forum: Networking &amp; Wireless
---

### Post by togo59 on 2009-03-21
I am trying to recover after my group file got overwritten and I cannot get the wireless applet to run. When I type ```
sudo nm-applet
```
it says
```
Failed to execute program
/lib/dbus-1.0/dbus-daemon-helper: success
```
Before the group file got wiped everything was fine. I have [[COLOR="Blue"]_another thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1095007") about that but this one is specific to the above question.

Thanks for your help (I know the forum is busy right now, lots of people have problems following the latest update).

---

### Post by 03taxi on 2009-03-21
sudo lets you run a program as the superuser (root).
yoour username has to be in the sudoers group for this to work.
first try to restore your group file then all should work again.

---

### Post by togo59 on 2009-03-22
Hi,

I am in sudoers, have no difficulty using sudo.

I am trying to repair group but don't know what gid/uid is needed to get nm-applet to fire up.

---

### Post by cthug on 2009-03-22
login as root.

---

### Post by togo59 on 2009-03-23
I had spurious 65534's in my passwd file.

Now fixed. Problem gone.

---

