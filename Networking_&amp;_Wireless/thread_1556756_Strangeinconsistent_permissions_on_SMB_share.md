---
title: "Strange/inconsistent permissions on SMB share"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by nulldozer on 2010-08-19
Hello everyone,

This one's hard to find on Google, so links to other relevant posts and sites are welcome.

When I mount an SMB/CIFS share using the GUI method (Places > Connect to Server > Windows Share) I can write files and retrieve/modify them later, no problem. I only have a problem with permissions when I mount the same network location using the mount command in the terminal. 192.168.1.2 is my NAS. Authentication is anonymous.
```
sudo mount.cifs //192.168.1.2/myShare /my/mount/location -o guest
```OR
```
sudo mount //192.168.1.2/myShare /my/mount/location -t cifs -o guest
```With either of the command line methods, the mount location's permissions are changed so that the owner is 'www' and any files I add are -rw-r--r--. chown does not work.

The GUI method is slow, it doesn't link very well with programs, and I can't add it to my fstab file. Please don't tell me to use that instead. All suggestions are appreciated, though.

---

