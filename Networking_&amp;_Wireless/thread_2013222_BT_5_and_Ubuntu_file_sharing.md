---
title: "BT 5 and Ubuntu file sharing"
date: 2012-06-30
forum: Networking &amp; Wireless
---

### Post by RaHorakhty on 2012-06-30
I set up file sharing on my Ubuntu 10.04.  I can now transfer large files to my BT 5 system, without any prob.  Whenever I transfer files from BT 5 to Unbuntu, however, the system somehow changes the attribute of the file by marking it as read only,which prevents from executing on Ubuntu.  I tried changing the attribute  to r/w on BT but no dice. any suggestions?

---

### Post by haqking on 2012-06-30
> **RaHorakhty said:**
> I set up file sharing on my Ubuntu 10.04.  I can now transfer large files to my BT 5 system, without any prob.  Whenever I transfer files from BT 5 to Unbuntu, however, the system somehow changes the attribute of the file by marking it as read only,which prevents from executing on Ubuntu.  I tried changing the attribute  to r/w on BT but no dice. any suggestions?

I imagine it is to do with the user, in Ubuntu you are likely an admin using sudo, in BT you are likely root (unless you changed the default setup) so the files are read only as they are owned by root.

Just a guess, as i dont know your filesystem or setup, mind you I have a killer headache so might be talking gibberish also as i cant think straight...LOL

Time to sign out.

Peadce

---

### Post by RaHorakhty on 2012-07-01
Thanks Haqking for trying Haqking! Eat some beans....it does wonders for a headache.

---

