---
title: "how to Unshare a share-folder in samba...?"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by tajiknomi on 2010-11-16
[SIZE=2]I had share my data-folder to another Computer,now i want to rivert(un-share) it..how can i  ?[/SIZE]

---

### Post by pricetech on 2010-11-16
If you installed system-config-samba, go to System - Administration - Samba and remove the share there.

If you manually edited your smb.conf file, make a backup, then edit again and remove the share there.

If you did it some other way, you'll have to undo it by "reversing the procedure" as it were if one of the above doesn't work.

---

### Post by tajiknomi on 2010-11-17
[I][SIZE=2]Thanks for your kind Reply....
i did it.... :P
[/SIZE][/I]

---

