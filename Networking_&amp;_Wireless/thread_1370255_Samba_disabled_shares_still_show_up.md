---
title: "Samba disabled shares still show up"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by Cuco3 on 2010-01-02
I have a problem where some samba shares I had set up before, but I've disabled already, are still showing up on network neighborhood with all the settings as if it was never disabled. I set up the share by right clicking > sharing options. It says the share for the two folders are not enable but they still show up on network neighboorhood. I've gone over the smb.conf and installed the smb GUI (which reports that there are no shares on my computer which it is the way i want configured). I've tried samba reloads and restarts with no luck. Has anyone heard of this before ? Google searches didn't reveal nothing.

---

### Post by Cuco3 on 2010-01-02
Nevermind, turns out that Nautilus handles shares when using "Sharing Options" on the context menu. I just went to "/var/lib/samba/usershares" and deleted the files in that folder that correspond to the particular share.

---

