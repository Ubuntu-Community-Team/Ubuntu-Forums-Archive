---
title: "best file transfer method"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by fela on 2009-07-11
I'm looking for the best file transfer method that I could have to automount a share, preferably / but at the very least /home/user. Yes, the username really is 'user' on my Linux server ;). Right now I'm making do with Samba (I have an entry in the fstab), but it only mounts the shares that I select, not like ssh/sftp, which mounts /.  This means that if I, say, wanted to share the CD drive of my server I need to create a Samba share of /media/cdrom0. Plus I'm sure there's more secure solutions, and Samba was developed for MS Windoze wasn't it? I don't think that's very applicable in a Linux server to Linux client setup!

I've tried sshfs, but you don't seem to be able to add an entry in /etc/fstab, and when I tried connecting to the server with that it mounted only the home directory. This does not happen in nautilus or the ssh CLI client, where you can see every single readable file on the system.

Any help? Please don't tell me to share the root directory through samba! :lolflag:

---

