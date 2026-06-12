---
title: "get permissions????"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by k3yb0red on 2011-07-31
i am trying to set a static ip. whenever i try to change /etc/network/interface it says i dont have the permissions to do this. i am the only user. how do i get permissions??????

---

### Post by sanderd17 on 2011-07-31
In Linux, you have a root user. No, not you, you're an administrator.

The root user is deactivated in Ubuntu because it was unsafe. The root user is able to change anything to the OS, so people kept logged in as root and were vunerable for malware.

Instead, in Ubuntu, you have the sudo command. An administrator can become root for one command by putting sudo (Super-User-DO) in front of it.

So if you try to change it via the command line, you just need to put sudo in front of it. e.g.

```

sudo gedit /etc/blablabla

```

But if you want the pure graphical way, there are also graphical variants of sudo. You have gksudo for Gnome and ksudo for KDE. So if you press ALT+F2 and execute
```

gksudo gedit

```

than gedit will also start in root mode. For the file manager in root mode, you can use
```

gksudo nautilus

```

But do remember that the root user has power over the complete computer. You have the power to delete everything with one simple command. So only do something if you know what you're doing.

If you want more info about the terminal and user rights in Linux, please read this: [http://linuxcommand.org/](http://linuxcommand.org/)

---

