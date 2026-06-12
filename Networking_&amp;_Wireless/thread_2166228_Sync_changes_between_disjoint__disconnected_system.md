---
title: "Sync changes between disjoint / disconnected systems via a remote server"
date: 2013-08-08
forum: Networking &amp; Wireless
---

### Post by mike666234 on 2013-08-08
I was wondering if it was possible to sync two directories - when both are not available at the same time.
Sure, I could use a server. The problem is that I'd have to keep my huge sync directory in that server - costly.
The solution would be to use a server - but to only store and sync the *changes* between the two directories.
When one communicates with the server, it would check for any existing unapplied changes from the other directory.
After syncing those, it would check for any local changes - and upload said changes to the server for the other directory when it checks.

Is this possible?

My use-case is that I have two machines, a Windows PC and a laptop running Ubuntu. On both are copies of my huge, ever-growing music collection.
Both are rarely on at the same time, and it's a pain to sync them any other way.

I know of rsync, but not sure if such a usage is within its capabilities.

---

### Post by Boab1993 on 2013-08-08
Hi there mike666234,

I believe it is possible, but to be honest id write a macro for it, i dont know any programs on here that do that specifically.

On another note, dropbox pretty much does that i think?

Hope this helps

---

