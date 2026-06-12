---
title: "Disable samba (Ubuntu Lucid)"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by peterson_espacoporto on 2010-11-04
I'm kind of lost. I need to disable user access to network shares. I've already uninstalled samba, smbclient, samba-common, winbind and even libgnomevfs-extra and nautilus is still able to access the shares! Isn't there an easy way to turn that network functionality in nautilus off?

---

### Post by peterson_espacoporto on 2010-11-04
Bump, please.. Any idea?

---

### Post by luvshines on 2010-11-05
You mean network shares of Windows machines, right ?
I think you need firewall rules to prevent access to destination port 445 and 139

---

### Post by sikander3786 on 2010-11-05
I think this needs to be done on the share server's firewall, not on the client.

This might help (not sure though).

Simply enable the default Ubuntu firewall, UFW.

```
sudo ufw enable
```

Set it to deny all connections by default.

```
sudo ufw default deny
```

Samba should be blocked by default, still you can,

```
sudo ufw deny samba
```

You can open any ports you need. Make sure your users don't know your password :)

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

