---
title: "How to setup Amarok to be the default player?"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by Spalatum on 2007-07-02
I would like to make Amarok open up when I hit my special music key on my keyboard. I have no idea how to do this, so I need some help. When I hit that key rhythmbox opens up.

Thanks in advance. ;)

---

### Post by Spalatum on 2007-07-03
Bumping this tread. I really want to get my music hot keys to work.

---

### Post by wconstantine on 2007-07-03
Do you use any software that comes with the keyboard? If you got that, open it up. I'm quite sure you should be able to change your bindings there. 

An alternative solution could be to install xbindkeys. This applications allows you to bind keys to commands.

To install this fire up you terminal and enter the following:

```
sudo apt-get install xbindkeys xbindkeys-config
```

After installation you need to configure your bindings. To do so you got to write xbindkeys-config in terminal and change the keys to the command amarok. There should be a window where you can press your key in order so you don't need to write whatever it's named.

I think it should work with a single key for a binding. If it works well then you can add xbindkeys to start at login every time. To do so, ... ehm. I actually don't know how you do that in KDE.. I guess you run KDE cuz you run amarok? Anyways for gnome, go System -> Preferences -> Sessions. Or you could type gnome-session-properties in the terminal. I think you can figure it out how to do next. ;)

Hope I helped. :popcorn:

---

### Post by blackened on 2007-07-03
See post number 7 in this thread: [http://ubuntuforums.org/showthread.php?t=292213]("http://ubuntuforums.org/showthread.php?t=292213").

This is a bug is hardcoded in Gnome, but should be fixed in Gutsy, or at least it's supposed to be.

---

### Post by Spalatum on 2007-07-05
Thanks a lot guys. This helped. Oh by the way I use gnome and The keyboard didn't come with any extra software. ;)

---

### Post by blackened on 2007-07-06
> **Spalatum said:**
> Thanks a lot guys. This helped. Oh by the way I use gnome and The keyboard didn't come with any extra software. ;)

It's highly unlikely that their software, if they had included it, would have worked with Linux anyway.

---

