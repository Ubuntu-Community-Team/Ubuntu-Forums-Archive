---
title: "shutdown from mythfrontend fails"
date: 2015-07-19
forum: Mythbuntu
---

### Post by Erik-NA on 2015-07-19
When selecting exit and shutdown in mythbuntu frontend, nothing happens. This used to work without any configuration. 

No errors, nor clues in either syslog or mythfrontend.log

And posts in the forum dealing with this are somewhat outdated (valid for older versions)

3.16.0-43-generic and MythTv 0.27

What can be wrong?

---

### Post by Lester_Burnham on 2015-07-20
Hi,

You might need to edit your sudoers file and add a line. Backup your /etc/sudoers file first if not confident.
Use this below to edit the file using nano
```
export EDITOR=nano && sudo -E visudo
```
Then paste these lines in below the admin section
```
# mythtv group
%mythtv ALL = NOPASSWD: /sbin/shutdown
```

Do a reboot and try again.

Lester

---

