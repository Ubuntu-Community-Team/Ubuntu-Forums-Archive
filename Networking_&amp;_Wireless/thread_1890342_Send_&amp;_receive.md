---
title: "Send &amp; receive"
date: 2011-12-03
forum: Networking &amp; Wireless
---

### Post by smss on 2011-12-03
Hi.
How to send/receive a file or folder to/from another computer on the terminal?(by command)
All the best.
Thanks.

---

### Post by 2F4U on 2011-12-03
If you can ssh into the other machine, scp or sftp would be able to do that. Else it depends on what OS the other machine is. If this are two Linux boxes and you need to do that more often, NFS may be an option. If one is Windows and the other is Linux, you can use Samba.

---

