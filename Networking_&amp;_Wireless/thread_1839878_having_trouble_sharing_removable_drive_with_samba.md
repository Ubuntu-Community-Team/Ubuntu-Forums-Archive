---
title: "having trouble sharing removable drive with samba"
date: 2011-09-06
forum: Networking &amp; Wireless
---

### Post by mistafeesh on 2011-09-06
Hi,

I've got a removable USB hard drive that I sometimes want to share over my smb network. I've tried adding it as a share but for some reason it doesn't work. It's called media and afaik mounts at /media/media but this mount point doesn't seem to want to work....

I also tried creating a symlink in another shared folder (this option would be preferable to me for simplicity)but it just shows up as a file. I tried adding 
'follow symlinks = yes
wide links = yes
unix extensions = no'

but this made no difference...


any ideas?

---

