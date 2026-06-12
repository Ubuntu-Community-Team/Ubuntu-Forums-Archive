---
title: "PC runs slow if network unplugged"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by Twelveone on 2010-12-16
Hi,

I'm not sure if this is the right place to post this but it is network related so here goes.

I've been asked to look at a system which is running slowly. It's running hardy on an intel Q9400 quad core CPU system which should be a pretty fast machine.

The most obvious symptom of this problem is that the terminal takes about 10 seconds to open instead of the usual fraction of a second.

What I've discovered so far is that the system has 2 network ports one configured to access the LAN and the other to connect directly to another piece of hardware using a different subnet. If the LAN is not connected the system runs slowly and if it is connected it runs at normal speed. It also makes no difference whether or not the second network port is connected.

I've looked at the system monitor and can see no abnormal network traffic or processes using a lot of CPU resources.

Does anyone have any ideas how to resolve this?

Thanks

Stewart

---

### Post by dandnsmith on 2010-12-16
As stated, it sounds as though the opening of the terminal causes some kind of network access.
Does the prompt involve the name of the host?
Possibly there is something in the .bashrc file?

Why not have a look in the resolver actions - the files are /etc/host.conf and /etc/resolv.conf, and you may need to change the order of entries if there is a 'files' entry which isn't first.

Best to check with man pages, as my knowledge is rather out-of-date I find.

HTH

---

