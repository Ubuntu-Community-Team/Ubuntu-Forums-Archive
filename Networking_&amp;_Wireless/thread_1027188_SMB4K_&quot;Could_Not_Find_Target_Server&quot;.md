---
title: "SMB4K &quot;Could Not Find Target Server&quot;"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by Kat of Zion on 2009-01-01
Im attempting to use SMB4K to create a mount point for my Network Drive (MyBook World).  Sadly, it gives me this error upon restart of the program.

mount error: could not find target server. TCP name Blah/blah not found
No ip address specified and hostname not found

Obviously SMB4K is trying to mount it without first scanning the smb network for the name.  So far, the only way around it is to put the Network drive's IP address in the /etc/hosts.  It would be nice to get SMB4k to learn this.

Kat
Hardy Heron

---

### Post by moe46 on 2009-04-30
Hi

Had the same problem there are a bunch of ways to fix it.
I found the easiest way was to use smb4k's Mount Manually 
function you just need the workgroup name commonly is MSHOME or WORKGROUP, the computers IP address and in the share box put //your_computers_name/share_name

Make sure you check the "Add this share to the bookmarks" box.

Then whenever you want to use the share you can open smb4k and just click the bookmark.

Hope it works,
Mushiden

---

