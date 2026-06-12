---
title: "Syncing Folders across a network"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by Jonny87 on 2010-11-08
I'm looking for a simple way keep two identical folders one on my laptop and one on my desktop up to date with each other so it doesn't matter which one I was last working from, they will both be equally up to date with the exact same copy of each file at the click of a button (or the running of a script).

I did have two different scripts that I used to use but I seem to be having trouble with them now, perhaps something is different in 10.10 that causing hiccups.

Does any one have any definite solutions?

---

### Post by P4man on 2010-11-08
Check out unison.

It doesnt support smb unless you you smbmount the shares, but it works great with ssh as well, which is very useful if you want to sync even when you are not home.

---

