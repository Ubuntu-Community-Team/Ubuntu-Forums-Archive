---
title: "'Who' is using SAMBA?"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by BassKozz on 2009-02-02
Is there a command that will let you find out who is accessing a samba share?
Similar to the 'who' command to find out who is logged onto a machine, but instead for SAMBA shares. Does a command like this exist?

Really my goal is to work this into a script that will shutdown my server at night so long as NO ONE is using the share.
TiA,
-BassKozz

---

### Post by JillSwift on 2009-02-02
[**smbstatus**]("http://linux.die.net/man/1/smbstatus") will do that.

_    _________edit              ______________________
Just found out Samba also has a"net" command.
"**net status shares parseable**" looks just about perfect for your needs :)

---

### Post by BassKozz on 2009-02-02
> **JillSwift said:**
> [**smbstatus**]("http://linux.die.net/man/1/smbstatus") will do that.

_    _________edit              ______________________
Just found out Samba also has a"net" command.
"**net status shares parseable**" looks just about perfect for your needs :)

Thanks Jill :D
Follow-up: [Need help creating an advanced shutdown script for powersaving?]("http://ubuntuforums.org/showthread.php?p=6662673")

---

