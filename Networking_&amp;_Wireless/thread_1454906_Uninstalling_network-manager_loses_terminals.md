---
title: "Uninstalling network-manager loses terminals"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by ene_dene on 2010-04-15
I use Ubuntu 9.10.
I need to have network right away because I put home directories on a server and use them via NFS.
To have network right away I needed to remove network-manager and put the configuration manually. It works, but after I removed the network manager, by pressing alt+F1,2,3,4 I don't get text terminals, that is I get them, but I don't have the option to login, just a cursor blinking. Sometime I need these terminals so I can kill a process that is crushing GUI, I don't want to do hard resets.

Why is that? Is there a better way for having network before GUI than editing /etc/network/interfaces and /etc/resolve.conf?

---

### Post by LeeDaugherty on 2010-04-15
Editing network/interfaces is how you setup a manual connection.  Hopefully a typo, but from GUI to terminal you have to hit ctrl-alt-F1.  Uninstalling NetworkManager shouldn't have anything to do with your getty's (TTYs).  I keep reading your post and I don't think I'm getting what the problem is?  Are you trying to login during boot before the gui loads?  That would explain all this and has a simple solution.

---

### Post by ene_dene on 2010-04-15
> **LeeDaugherty said:**
> Editing network/interfaces is how you setup a manual connection.  Hopefully a typo, but from GUI to terminal you have to hit ctrl-alt-F1.  Uninstalling NetworkManager shouldn't have anything to do with your getty's (TTYs).  I keep reading your post and I don't think I'm getting what the problem is?  Are you trying to login during boot before the gui loads?  That would explain all this and has a simple solution.

You're correct, it was a typo, I meant alt+ctrl+Fn, n=1,2,..6.
I have found the error. While editing /etc/network/interfaces I haven't put the line:
```
auto lo
iface lo inet loopback
```
and some programs couldn't connect to localhost. Now, everything works good.

---

