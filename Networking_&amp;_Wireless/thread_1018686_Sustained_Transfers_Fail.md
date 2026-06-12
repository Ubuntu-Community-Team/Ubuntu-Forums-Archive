---
title: "Sustained Transfers Fail"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by Kissell on 2008-12-22
So, I recently installed Ubuntu on another box and formatted it's data partition using XFS (first time using XFS).  Seems to work okay, except I'm trying to fill up that data partition by copying a bunch of data to it from another Ubuntu server.

Everytime I initiate the copy it works great for maybe 30 seconds, and then it hangs and times out.

It doesn't matter what program I use, I've tried using different ftp clients, using rsync, using mirrordir, they all begin then fail soon after it started, after it looks like it's going great.

It doesn't matter what server I initiate the transfer on, server1 or server2, no matter who is pushing and who is pulling, it still dies...

My guess is that linux is seeing this massive network pounding as a potential attack instead of a legitimate transfer.  I know it's Ubuntu because I put the servers on a private gigabit network, just the two of them, so no external firewall or IDS is getting in the way.  And since I just built the new server it must be something someone loaded on the old one (or maybe it has something to do with XFS)...  i dunno, but i'm stuck, looked at everything I can think of.

---

