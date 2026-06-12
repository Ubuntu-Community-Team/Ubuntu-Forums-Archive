---
title: "Sync iPod Wifi (SSH?)"
date: 2010-10-07
forum: Multimedia Software
---

### Post by Zortrox on 2010-10-07
I've scoured almost everywhere looking for a way to sync my iPod Touch (synonymous with iPhone at the moment) with Rhythmbox.  Yes, I know there are guides all out there, but they are for older firmwares.  Whenever I connect my iPod, it mounts into:
```
~/.gvfs/"(My iPod Name)"
```I can connect to my iPod via SSH and set it to mount virtually anywhere through "sshfs", but I can't get it to mount into the /.gvfs folder.  For some reason I don't have permission to even make a directory inside of that folder even as root.  I can't even chown the dang folder.  (By the way, I know that the /.gvfs mounted, but I don't know what mounts the folder (I ran "mount" and saw it in terminal))

In summary:
  How can I get permissions into the /.gvfs folder?  OR
  Can I change where my iPod is automatically mounted and still have Rhythmbox detect it?

---

### Post by Zortrox on 2010-10-07
Just a little update:

I found that I can use:
```
dbus-launch bash
/usr/lib/gvfs/gvfsd -r &
gvfs-mount sftp://root@("My IP Address")
```to connect to gvfs over an sftp connection, but it always gives me this error.

```
** Message: secret service operation failed: Did not receive a reply.
Possible causes include: the remote application did not send a reply, the message
bus security policy blocked the reply, the reply timeout expired, or the network
connection was broken.
```All I have for the "My IP Address" part is just my IP address.  Do I need to append anything to get this to work like a port or slashes, etc?

Thanks in advance for the help!

---

