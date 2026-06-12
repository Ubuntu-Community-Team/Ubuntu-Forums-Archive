---
title: "Pam_mount, fuse, and smb. How?"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by Bufke on 2011-03-28
I'd like to use fuse instead of cifs for [this]("https://bugs.freedesktop.org/show_bug.cgi?id=35751") reason to auto mount folders using pam_mount. I know gvfs can mount smb just fine. I know gvfs uses fuse. So it should be possible to do something like

<volume fstype="fuse" path="smb://server/share" mountpoint="~/my_mount_point" />

This does not work, I assume my syntax is incorrect or I don't understand something.

---

### Post by Morbius1 on 2011-03-28
Never used pam_mount - never heard of it before your post so consider this a bump.

Did you try adding the option nobrl to you cifs mount expression. From man mount.cifs:
> **nobrl**
           Do not send byte range lock requests to the server. This is
           necessary for certain applications that break with cifs style
           mandatory byte range locks (and most cifs servers do not yet
           support requesting advisory byte range locks).


---

### Post by Bufke on 2011-03-28
Perfect! Thanks!

---

