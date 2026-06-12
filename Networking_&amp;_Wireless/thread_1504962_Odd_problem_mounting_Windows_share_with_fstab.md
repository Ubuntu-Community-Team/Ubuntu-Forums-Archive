---
title: "Odd problem mounting Windows share with fstab"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by applerock79 on 2010-06-08
Hello I cannot mount my windows share automatically with fstab and have the files be R/W. They are only mounted as read-only.
I have tried several dozen commands in the fstab file with many mount points and different users. The share is on a Windows 2000 server, but NOT a domain controller.

Thing is, using the Places|Connect To Server|Windows Server menu selection, it works fine. And when I use that, the share shows up on the desktop. However, in some programs I cannot see the share in the open/close dialog boxes. I can however go to /mnt/server to see them if I mount them in fstab. The files just open as "read only" that way however.

Have tried... on last line of fstab mount command.....rw option, +777 option, using IP address of server, using server name. 

Same result (as fstab) if I do a manual mount command, then a mount -a. Mounts Ok, just as "Read only".
ex: sudo mount -t smbfs //192.168.1.xxx/sharename /media/server -o username=xxxxxx,password=xxxxxxxx
 
This has been the case with Ubuntu 8.04 until my current one, 9.10. Ubuntu (if you are listening) really needs to make this easier. It truly is basic network stuff that for some reason is rather difficult to do. Read only access is not actual network access and my other option (having to manually connect via the drop-down menu) each time I boot up is a pain.

What is different about that "connect to server" option on the menu that makes it work? It'd be great if there was a check box there that said "remember this connection". Then all would work fine.

Thanks for any help you could provide, been chasing my tail with this for a while now.

---

### Post by Morbius1 on 2010-06-08
> Thing is, using the Places|Connect To Server|Windows Server menu  selection, it works fine. And when I use that, the share shows up on the  desktop. However, in some programs I cannot see the share in the  open/close dialog boxes.> What is different about that "connect to server" option on the menu that  makes it work? It'd be great if there was a check box there that said  "remember this connection". Then all would work fine.When you do a "Connect to Server" it actually issuses the following command:
```
**gvfs-mount **[smb://192.168.1.xxx/sharename]("smb://server/share_name")
```The problem with seeing it from a given application is that it mounts it to a hidden mount point ( why I do not know ) located at :
> /home/your_user_name/.gvfsNote the "." before the "gvfs" indicating a hidden directory. One way out of this is to create a symbolic link from the hidden mount point to a "non-hidden mount point".

As for "remember this connection" you could "Bookmark" it in Nautilus  - so when you need to mount it again it will show up under "Places" in Nautilus. You can also automount it ( sort of the gvfs equivalent of an fstab entry ) by using this technique:

**Map Windows Shares Permanently with GVFS: **[http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

---

### Post by capscrew on 2010-06-08
@ applerock79,

> sudo mount -t smbfs //192.168.1.xxx/sharename /media/server -o username=xxxxxx,password=xxxxxxxx


The **smbfs **routines have been superseded with **cifs**.  Try this```
sudo mount -t [COLOR="Red"]**cifs**[/COLOR]//192.168.1.xxx/sharename /media/server -o [COLOR="red"]**rw **[/COLOR]username=xxxxxx,password=xxxxxxxx

```

@ Morbius1,

> The problem with seeing it from a given application is that it mounts it to a hidden mount point ( why I do not know ) located at : **/home/your_user_name/.gvfs**

That's just the way the Gnome dev's decided it should be.  It is mounted in the Gnome Virtual File System.

FYI -- not all apps are GVFS aware which is why the OP has noticed the irregularities between the different mounts.

---

### Post by applerock79 on 2010-06-14
Thanks, that link worked.
I'm going to experiment and try a mount command with a mount point. ex at /media/servershare. See if that'll work, then it will accomplish what I need. Have a shared folder accessible from any program at /media/servershare.

---

