---
title: "Folder name different on Network than on PC."
date: 2012-10-02
forum: Networking &amp; Wireless
---

### Post by StephanG on 2012-10-02
Hi guys,

I've got a folder that I'm sharing over the network with Samba, but for some reason I can't quite fathom one of the sub-folders' name is perfectly fine on my PC, but when I'm viewing the folder over Samba, the name changes to "FG5HLA~7".

I've also noticed that when I copy it onto an external, other computers often have difficulty opening the file.  I've already tried to rename it and it's internal files.  If anyone could help me understand what's going on, I would appreciate it.

P.S.  It was only that single folder and it's internal files for a very long time.  But now, another folder has popped up with similar behaviour.

---

### Post by nothingspecial on 2012-10-04
*Thread moved to **Networking & Wireless**.*

---

### Post by albandy on 2012-10-04
> **StephanG said:**
> Hi guys,

I've got a folder that I'm sharing over the network with Samba, but for some reason I can't quite fathom one of the sub-folders' name is perfectly fine on my PC, but when I'm viewing the folder over Samba, the name changes to "FG5HLA~7".

I've also noticed that when I copy it onto an external, other computers often have difficulty opening the file.  I've already tried to rename it and it's internal files.  If anyone could help me understand what's going on, I would appreciate it.

P.S.  It was only that single folder and it's internal files for a very long time.  But now, another folder has popped up with similar behaviour.

In your smb.conf file, add this in [global] section:
mangled names= no

---

