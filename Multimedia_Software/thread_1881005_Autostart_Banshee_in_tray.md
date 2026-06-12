---
title: "Autostart Banshee in tray"
date: 2011-11-14
forum: Multimedia Software
---

### Post by Apolyonn on 2011-11-14
I have Banshee set to autostart when I log in; but I'd like it to start in the background, either as a Notification area or Indicator icon.  I posted a similar regarding Tomboy about a year ago, but the --tray-icon suffix doesn't work in this case.

Any advice?

Also: The thread prefix is all variants, but I'm running this on Xubuntu 11.10.  If for some reason the interface has anything to do with the startup commands, I can change the thread preifx.

---

### Post by jerrrys on 2011-11-16
you should be able to open "startup applications" from your main menu and add to startup.

the startup command would be

banshee-1 --redirect-log --device-activate=%u

---

### Post by Apolyonn on 2011-11-18
> **jerrrys said:**
> you should be able to open "startup applications" from your main menu and add to startup.

the startup command would be

banshee-1 --redirect-log --device-activate=%u

With that command, Banshee will not even load at startup :\


EDIT: I ran across [this thread]("http://ubuntuforums.org/showthread.php?t=762358"), where someone basically asked the same question and got a working solution.  The command is:

```
banshee --hide
```

---

