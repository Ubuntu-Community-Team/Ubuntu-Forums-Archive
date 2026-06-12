---
title: "File sharing between Ubuntu and Mac OSX"
date: 2013-04-06
forum: Networking &amp; Wireless
---

### Post by c-m on 2013-04-06
What's the best way of sharing files between ubuntu 12.04+ and OSX Mountain Lion?

I'm currently running Samba 3.6.3 and it works great between ubuntu and windows, and other linux distros but is absolutely dog slow on my mac.

The same samba server is also running a DAAP music server which is lightening fast when accessing music via the Mac, so the problem here is clearly with samba and/or apple's implementation of it.

So if samba is a no go, what alternatives do I have?

---

### Post by Kirboosy on 2013-04-06
You could always use SCP (secure copy, it uses SSH). Maybe an upgrade to Samba4 would help.

 If you want to leave Samba all together look into [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") or [SCP]("https://help.ubuntu.com/community/SSH/TransferFiles")

~Caboose

---

