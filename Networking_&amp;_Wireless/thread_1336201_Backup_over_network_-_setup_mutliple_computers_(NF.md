---
title: "Backup over network - setup mutliple computers (NFS, NIS, SMB?)"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by gforster on 2009-11-24
I have a computer lab in our K-12 school with 30 ubuntu desktops. There is a windows server that really only supplies the subdomain that the desktops are on. Things are going rather well over all and I am learning much as I go. Right now I have it setup that I can easily administer the systems via SSH. 

All computers currently use the same logon for the students (normal desktop user without any administrative priveleges) and that account is always left on. This is because the computer teacher for the younger students threw a tantrum (yes, like a child) when I said I wanted to have each student use an individual login. "It was never that way before. . .it will be too hard. . .they will forget. . .blah, blah, blah." Of course, she has taken the switch to ubuntu quite well, so I think she could handle individual logins and teaching students responisbility. I could even have the youngest (1st and 2nd grade) students all have the same login. I believe to do this I would need an NIS server.

Here is my real need - backups. Even if I leave things set as they are, I still need to backup the home directories (monthly, weekly, nightly). Should I do this via Samba or NFS? How do I figure out how much space I would need? What is the best tool to use to automate this process on all of these computers? 

One of the great things I have found about linux is that there are multiple ways to do the same thing. Some work better for certain situations. To someone new to this realm, though, it can get very confusing very quickly.  I just need a little guidance and pointing in the right direction.

Thanks

---

### Post by stasheck on 2009-11-24
I'd go for rsync differential copies. Read about rsync, you'll find a lot of info and many recipes - one of them should suit you.

---

### Post by memilanuk on 2009-11-24
BackupPC should be able to do the trick... and it supports backups over Samba for the machines that need it, or rsync+ssh for *nix clients.

---

