---
title: "TightVNC Connection - Can only see wallpaper?"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by MuddBuddha on 2009-07-09
I'm logging into my 9.04 box at home from my XP box at work using TightVNC.  Once it connects, all I can see is my wallpaper and no panels.  Right clicking does nothing, but the mouse moves fine.

Don't get me wrong, I like the wallpaper I chose, but I was hoping for a little more functionality. ;)

If you have any suggestions for me, let me know.

---

### Post by superprash2003 on 2009-07-09
in ubuntu press alt+f2 and type gconf-editor and go to desktop-gnome->remote_access and make sure view_only is unchecked

---

### Post by djschwartz on 2009-07-31
Any luck figuring this one out?  I've got the same issue.  Trying to use TightVNC on Vista to connect to Ubuntu.  I get a view of whatever is up on the Ubuntu screen and I can move the mouse around and click.  On the Ubuntu machine everything is working, but my viewer just doesn't ever refresh.

---

### Post by djschwartz on 2009-08-01
After a little more searching I found the solution to this one here:

[http://ubuntuforums.org/showthread.php?t=810592]("http://ubuntuforums.org/showthread.php?t=810592")

Select System -> Preferences -> Appearance, Visual Effects tab, and disable effects.  Everything works great now!

---

