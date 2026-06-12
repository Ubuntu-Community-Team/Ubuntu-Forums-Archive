---
title: "More samba charset issues"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by vertespain on 2006-07-08
I have a writable directory shared in samba on my ubuntu server. The directory is on a fat-32 volume, though I'm not sure if that makes a difference. When I try to copy some files with French accents in their names from my OSX machine onto the ubuntu server, the file names always get mangled. I've seen some issues with charsets and samba on the forums, but they were all about mounting filesystems. Anyone have a tip about what to do in this case?

---

### Post by vertespain on 2006-07-09
Problem solved. Just appended the charset suggestions in other posts to smb.conf.

---

