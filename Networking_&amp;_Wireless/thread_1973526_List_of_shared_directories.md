---
title: "List of shared directories?"
date: 2012-05-04
forum: Networking &amp; Wireless
---

### Post by Alan.Brown on 2012-05-04
Somewhere there must be a file with a list of shared directories that I can edit.

Where is it?

TIA

Alan

---

### Post by papibe on 2012-05-04
Hi Alan.Brown.

If you are referring to samba shares, run this command to see your own shares:
```
smbclient -L localhost
```
And to see all accessible shares over the LAN:
```
smbtree
```
I hope that helps.
Regards.

---

### Post by Alan.Brown on 2012-05-04
Thanks.  That helped a lot.   I deleted a directory without 'unsharing' it first.  On the net it showed - but I couldn't delete it.

I deleted the entry in **/etc/samba/smb.conf.  **Problem solved.

Alan

---

