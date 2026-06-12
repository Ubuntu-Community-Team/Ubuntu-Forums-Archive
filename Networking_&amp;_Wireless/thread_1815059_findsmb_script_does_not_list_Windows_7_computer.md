---
title: "findsmb script does not list Windows 7 computer"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by r.darwish on 2011-07-30
When running findsmb in my local workgroup network, the script only lists computer running Samba under Ubuntu. The rest of the computers, which are running Windows 7 are not listed.
As I understand, and I may be wrong, Windows 7 computers no longer support workgroups.

However, [Smb4K]("http://smb4k.berlios.de/"), which to my understanding uses the same Samba libraries as findsmb, does list all computers on the network, including the ones running Windows 7.

I am looking for a similar CLI tool that shows all computers on the network.

---

### Post by r.darwish on 2011-08-08
*bump*
Any ideas? :)

---

### Post by bsync on 2011-09-15
I noticed the same thing. In addition when I try smbtree I get:

Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED

---

