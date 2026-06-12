---
title: "smb access from applications"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by zakarra on 2010-02-22
Hi,

I'm relative newbie in Ubuntu. My problem is that i have a network hd shared in my LAN. I can access it with nautilus but when i want to open a dir from an application i cant access,  smb:// doesn't do nothing. 

For example, i have a ubuntu server in a vmware machine y shared network folder but i can't open this with vmware player because in open file dialog doesn't appear.

Please help me configuring this. 

thanks!

---

### Post by maweki on 2010-02-22
The folders are actually mounted to "/home/[username]/.gvfs"

applications should be able to use those folders.

But be aware that some programs don't like it when they are accessing files from or writing to slow devices (like a share over the internet).

---

### Post by zakarra on 2010-02-22
but the folders are not mounted.

how can i mount network directories?

---

### Post by Morbius1 on 2010-02-22
> My problem is that i have a network hd shared in my LAN. I can access it with nautilus but when i want to open a dir from an application i cant access, smb:// doesn't do nothing.The act of accessing the share in Nautilus causes nautilus to mount the share:
> maweki
The folders are actually mounted to "/home/[username]/.gvfs"
So it's a two step process:

(1) Access the share from Nautilus
(2) Access the share using your application by going to "/home/[username]/.gvfs"

---

### Post by Jive Turkey on 2010-02-22
You might find it helpful to use cifs to mount the share.  You can tell ubuntu to mount it at bootup every time by putting the proper cifs entry into the /etc/fstab.

You should read this guide:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

If you need clarification on the guide just ask:)

---

### Post by zakarra on 2010-02-23
> **Jive Turkey said:**
> You might find it helpful to use cifs to mount the share.  You can tell ubuntu to mount it at bootup every time by putting the proper cifs entry into the /etc/fstab.

You should read this guide:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

If you need clarification on the guide just ask:)


Thanks to all! specially to you jive turkey, this torial looks like what i need. If i need something more i'll be back. 

thanks a lot.

---

