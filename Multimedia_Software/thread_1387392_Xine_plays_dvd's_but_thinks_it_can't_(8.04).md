---
title: "Xine plays dvd's but thinks it can't (8.04)"
date: 2010-01-21
forum: Multimedia Software
---

### Post by Horza on 2010-01-21
In Hardy Heron, after installing xine and the usual stuff, and setting xine as the default dvd player in /etc/gnome/defaults.list in the usual way, and also linking /dev/dvd to /dev/dvd2, when I pop in a commercial dvd for autoplay, or select xine from the context menu to play it, it starts to play fine, but also produces the "source can't be read" messagebox, which goes away after being OK-clicked 10 (exactly!!) times.

Launching xine directly from the application menu does not produce this problem.

So, does anyone know how to prevent this annoying messagebox from appearing?

---

### Post by mc4man on 2010-01-21
While I don't use hardy anymore did spend a bit of time on such things

I guess it was ok to use defaults.list to set xine as default player, though it isn't the preferred method. (editing that line more than once can also lead to issues..

Also no a fan of symlinking /dev links - better to change in cd.rules or change in player (xine allows that in it's preferences- "masters of the known universe" experience level


Anyway the issue as far as autoplay is you're using the default lauch command which is not suitable for autoplay. It needs to be xine dvd:// instead of xine %U

Now xine dvd:// as a launch command isn't good for the default so you need to make a 'new' xine .desktop just for autoplay - like xine-dvd.desktop and a new name - like xine1

Method is here if you wish to read, I don't think already setting xine.desktop in defaults.list willl be an issue, though I'd leave that file alone at this point. 
Your new default choice will be xine1 (make sure to change the name when editing xine-dvd.desktop

[http://ubuntuforums.org/showthread.php?t=914043](http://ubuntuforums.org/showthread.php?t=914043) post 6
A bunch of related hardy stuff in same vein, some may be a bit outdated, haven't edited in quite a while
[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

---

