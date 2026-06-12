---
title: "Geany changes owner after save on sftp"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by MeanEYE on 2009-02-09
Hi every1,

I've been using geany for some time now and really like it... but recently since my company started using remote servers we've run into some issues.

I connect to SSH2 or SFTP using native gnome support or nautilus. Open PHP file for editing and after applying changes... I save the file...

After a while I've noticed that geany changes owner of files after save. No matter what owner:group file was geany saves it to root:root (probably because am logged in as root)...

Anyone has any idea about this...

---

### Post by MeanEYE on 2009-02-12
I've solved it on another way... 

Turns our that gvfs changes owner and rights everytime file is saved or copied using this protocol...

I haven't been able to find solution for this so workaround is in order. Fetch something that's called sshfs... mount remote directory locally and there you have it...

---

