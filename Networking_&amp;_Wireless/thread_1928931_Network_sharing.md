---
title: "Network sharing"
date: 2012-02-21
forum: Networking &amp; Wireless
---

### Post by Herophantom on 2012-02-21
Hello,
Im pretty new to Ubuntu, but I do have some knowledge and have used it to a small degree before. Last weekend, i set up a new Ubuntu server for the first time, and so far im getting most things figured out ok. Right now, im having an issue sharing a few folders with my local network. Im hosting 2 simple websites for my parents, which is working just fine, but i want to allow them to upload any changes themselves.

When i try to use the share options in the GUI, i get this error:

Samba's testparm returned error 1: Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
WARNING: state directory /var/lib/samba should have permissions 0755 for browsing to work
WARNING: cache directory /var/cache/samba should have permissions 0755 for browsing to work

can i get a little guidance on this?

---

### Post by Herophantom on 2012-02-22
UPDATE:
Im figuring more out about how to work with Ubuntu and repaired the file permissions the error code was referencing. So now it seems as it the service is running and the files i need are shared. But i cannot seem to access them from my windows computer. I have just the smbpasswd command to add my main user name to the list with no password. When i access the server with its IP address on my network, it asks me for the credentials but when i put it in, it will seem to accept it but doesn't show any files.

---

### Post by Herophantom on 2012-02-23
well, fixed it, on my own.

---

