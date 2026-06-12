---
title: "Possible to mount/umount volumes when SMB clients connect/disconnect (or idle)"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by brouer on 2011-01-20
Is it possible to defer actually mounting a volume on the server, until a Samba client connects to the server and tries to access it?

Similarly, can it automatically be unmounted when the last client disconnects or has been idle for some time?

Edit:
Of course there is. "preexec" and "postexec".

Should have tried that one more Google attempt before posting. :)

---

