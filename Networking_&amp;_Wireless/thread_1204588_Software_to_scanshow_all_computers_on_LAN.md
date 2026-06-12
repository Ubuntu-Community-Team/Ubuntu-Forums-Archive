---
title: "Software to scan/show all computers on LAN"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by pythonscript on 2009-07-04
Is there a package (preferably from the repositories, of course) that will display all the computers it can access (maybe ping is a more accurate word) on my LAN? I'm looking for something where I can specify a port, and it'll show me all the ip addresses, plus maybe any other information like os, etc, of computers that have that port open. Thanks!

EDIT:  Posted too soon. nmap will do exactly this. Sorry about the redundant post.

---

### Post by wojox on 2009-07-04
I use nmap

It's in the repo's.

---

### Post by Tutigan on 2009-07-04
> **wojox said:**
> I use nmap


Nmap is good, I use it too.
Not sure if there are many others, but it's the best I have found on Ubuntu and Windows

---

### Post by swerdna on 2009-07-05
smbtree is good too.
smbtree -N shows like this:
[HTML]john@kubu904:~> smbtree -N
SWERDNA
        \\UBUNTU904
                \\UBUNTU904\IPC$                IPC Service ()
                \\UBUNTU904\ubufiles
        \\SUSE111
                \\SUSE111\HL2040                HL2040
                \\SUSE111\IPC$                  IPC Service ("")
                \\SUSE111\QuickBooks
                \\SUSE111\linuxshare
        \\DRAGAVISTA[/HTML]
and smbtree -NS shows just the servers:
[HTML]john@kubu904:~> smbtree -NS
SWERDNA
        \\UBUNTU904
        \\SUSE111
        \\DRAGAVISTA[/HTML]

---

