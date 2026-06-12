---
title: "Samba - with a twist"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by snorkytheweasel on 2010-11-17
As is often asked, "how do I get samba to recognize my windows network shares"? But this problem is a bit different.

I have 2 Ubuntu machines, sitting side-by-side - same subnet, same windows domain, both using Dolphin as a file manager. 
[LIST=1]
[*]One is old and tired (the hardware, not the OS) and needs to go to the recycling bin. It's running Gutsy (after upgrading from Breezy). 
[*]The other is fairly new, much faster, and the proud possessor of a big hard drive - which is what it needs, since it operates primarily as a file server. It runs Maverick.
[/LIST]
The problem is that 
[LIST]
[*]On the old machine, Samba sees all of the windows domains and sees all of the Windows shares on each. I must have tweaked that one correctly. 
This old one even sees the new computer in the appropriate Windows share.
[*]On the new one, Samba sees only one windows domain, and sees no shares - other than itself - on that one windows domain.
[/LIST]
I've tried tweaking smb.conf, but nothing I've tried works. I copied the functioning smb.conf from the oldie-but-goodie to the newbie, but the result is the same: Samba sees one windows domain, and sees no shares on that one windows domain.

The functioning smb.conf.txt is attached. I had to change the name to get the forum software to accept it (pretend the ".txt" isn't there.:) )

Ideas, anyone?

---

### Post by snorkytheweasel on 2010-11-18
Attached is a slightly edited smb.conf (uploaded as smb.conf.txt)

In this "version" of the file, lines edited from default smb.conf are highlighted: there are 2 changes:
[LIST]
[*]old:
```
workgroup=WORKGROUP
; security=user
```

[*]new:
```
## -------------------------------------changed this line
workgroup = OHSD
## --------------------------------------

## -------------------------------------changed this line
security = domain
## --------------------------------------
```
[/list]

---

