---
title: "Nautilus Won't Connect To Windows Shares"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by derklempner on 2010-08-17
After running updates earlier today, none of my Ubuntu-based computers can connect to any Windows shares in Nautilus.

Samba is running and working fine; I can access the shares via web browser using ***smb://hostname***, so I know it's not an issue with Samba not working.  Also, the two Windows-based computers can see each others' shares, including printers.

Anybody else having this problem?  Any solutions?

---

### Post by lukeiamyourfather on 2010-08-17
I noticed there was a Samba update on my machine earlier today. It asked if I wanted to replace the configuration files or keep them. Perhaps you lost some configuration data in the process. Or maybe the services didn't start after the update, tried restarting? Also I don't think going to a smb:// address in a web browser uses Samba, probably something in the browser itself like going to a ftp:// address.

---

### Post by derklempner on 2010-08-17
> **lukeiamyourfather said:**
> I noticed there was a Samba update on my machine earlier today. It asked if I wanted to replace the configuration files or keep them. Perhaps you lost some configuration data in the process. Or maybe the services didn't start after the update, tried restarting? Also I don't think going to a smb:// address in a web browser uses Samba, probably something in the browser itself like going to a ftp:// address.
No, I don't think I lost any configuration files because I don't have Samba shares set up on every computer.  The ones that do have Samba shares are still accessible, even via Nautilus.  It's just the Windows computers (one is Vista, the other is Windows 7) that none of my Ubuntu systems can access.

Also, the ***smb://*** wouldn't work without **smbclient** installed on the machine.

---

### Post by derklempner on 2010-08-17
Bumpity bump.

---

