---
title: "No internet connection"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by oshirowanen on 2011-01-10
I have a dual boot computer, ubuntu 10.04 and windows xp.  Up until today, the internet connection had never been a problem for both OSes, but today, ubuntu thinks I am disconnected.  I booted to xp and the connection works fine.  Reconnecting via the network icon at the top right corner of the screen does not make a difference, I just get a pop-up saying that I am disconnected, and the network icon has a red exclamation mark on it.

I have a wired connection, not that that should matter, as the connection works as normal on xp, and it worked as normal on ubuntu until today.

What has happened?

---

### Post by PatchesTheCaveman on 2011-01-11
Go to Applications > Accessories > Terminal, and type each of the following commands in the black box that appears, pressing Enter after each one:
```
nm-tool
ifconfig -a
lshw -C network
```
Copy and paste the output into a reply to this thread.  We can use that information to see what's going on.

---

