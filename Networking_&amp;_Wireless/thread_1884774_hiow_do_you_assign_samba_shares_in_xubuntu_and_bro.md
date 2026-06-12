---
title: "hiow do you assign samba shares in xubuntu and browse network?"
date: 2011-11-21
forum: Networking &amp; Wireless
---

### Post by skinfish on 2011-11-21
hiow do you assign samba shares in xubuntu and browse network?

---

### Post by Toz on 2011-11-22
> **skinfish said:**
> hiow do you assign samba shares in xubuntu... 
You need to use samba (See: [https://help.ubuntu.com/community/Samba]("https://help.ubuntu.com/community/Samba")). Make sure it is installed. You can either manually edit the /etc/samba/smb.conf file or use a front-end tool like system-config-samba (look for it in the Software Centre, or from a command pronpt:
```
sudo apt-get install system-config-samba
```
If you're using a firewall, make sure its adjusted accordingly.


> ...and browse network?
Make sure you have gvfs-backends installed. Look for it in the Software Centre or:
```
sudo apt-get install gvfs-backends
```
You will then get a "Network" entry in Thunar that will allow you to browse network shares. You can also use "gigolo" (I believe its installed by default) to specify shares that you want to connect to automatically.

---

