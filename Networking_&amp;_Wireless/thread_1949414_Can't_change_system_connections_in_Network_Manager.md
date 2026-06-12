---
title: "Can't change system connections in Network Manager"
date: 2012-03-30
forum: Networking &amp; Wireless
---

### Post by aneganov on 2012-03-30
Ubuntu 11.10/gnome 3/gnome-shell

I can't change anything in system connections.
For example, I open Wired connections, go to Configure, change anything (for example checking off "Auto" checkbox), then press Save... and after this a black auth window popups and suddenly disappears not allowing me to type password!


See this demonstration I've recorded:
[http://www.screencast.com/users/Onkeltem/folders/Default/media/6ea518fd-b2bb-4be7-8f8a-23545b4e8e5d](http://www.screencast.com/users/Onkeltem/folders/Default/media/6ea518fd-b2bb-4be7-8f8a-23545b4e8e5d)

This is what I get in /var/log/auth.log:

```
Mar 30 13:32:12 alpha polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session2 FAILED to authenticate to gain authorization for action org.freedesktop.NetworkManager.settings.modify.system for system-bus-name::1.60 [<unknown>] (owned by unix-user:fantomas)
```

---

### Post by pellyhawk on 2012-03-30
I met the same problem before. Finally I found /etc/network/interfaces have some issues. Maybe you should check it.

---

### Post by aneganov on 2012-03-31
> **pellyhawk said:**
> I met the same problem before. Finally I found /etc/network/interfaces have some issues. Maybe you should check it.

It contains two lines:

auto lo
iface lo inet loopback

Nothing more

---

### Post by praseodym on 2012-03-31
Try to start the applet from terminal:

> gksu nm-connection-editor

---

### Post by jgooch on 2013-04-01
> **praseodym said:**
> Try to start the applet from terminal: This seriously saved my life. Not really, but I was seriously stuck trying to fix my search domain and this solved  my problem. 

Network Manager should prompt for the root password if root access is required to change network settings. The update manager prompts you ( too many times ) when updating software, so why doesn't NM? Consistency is important. :)

---

### Post by Iowan on 2013-04-02
From the Code of Conduct:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

