---
title: "How to add network shares to Quod Libet library"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by Endolith on 2007-10-29
How do I import folders from ssh:// or smb:// shared files to Quod Libet?

---

### Post by hugmenot on 2007-10-29
Do you see these shares in your sidebar? When you click them do their contents show up? I know that QL depends on Gstreamer-GnomeVFS, that might mean that Gnome shares are supported.
Otherwise you might need to mount your shares via real mount points.
I share my music over an NFS share, and that works beautifully.

---

### Post by Endolith on 2007-10-30
> **hugmenot said:**
> Do you see these shares in your sidebar?

No.  If I try to add a folder or file, it only shows local things.

---

### Post by hugmenot on 2007-10-30
Then you must access the shares with real mounting.

For Samba you would mount with cifs and for SSH with sshfs over fuse.

---

### Post by Endolith on 2007-11-08
> **hugmenot said:**
> Then you must access the shares with real mounting.

For Samba you would mount with cifs and for SSH with sshfs over fuse.

Is there an "easy way" for this?  (Nautilus, GUI, etc.)

I don't like rubbing sticks together for hours and then finding out there was a pack of matches in my back pocket. :-)

---

### Post by hugmenot on 2007-11-09
Not really, but it&#8217; considerably easy. There is the a way to access Samba shares with Nautilus as you know (i.e., via GnomeVFS), but the actual apps have to support the method. With the next Gnome you will likely be able to use all apps, since they&#8217;ll switch to a better implementation of vfs. Meanwhile you can learn how the traditional mounting is done. It&#8217;s also more efficient.

Create a mount point with mkdir in your /media folder (say musicshare)
Open the file /etc/fstab as a superuser and add a line in the end
```
//<musicpc>/<share> /media/<musicshare> cifs   noauto,credentials=/etc/samba/user,rw,uid=<myusername>,iocharset=utf8   0   0
```
If you make that auto, it will mount itself at boot, otherwise you have to mount it, e.g. through Nautilus. In place of "credentials=/etc/samba/user" you could write "username=<windowsuser>,password=<windowspw>" but that&#8217;s no good since fstab is world readable. Just create the file "/etc/samba/user" with the lines```
username=<windowsuser>
password=<windowspw>
```
and make it not world-readable by saying
```
chmod 600 /etc/samba/user
```

Now your mount is properly listed in fstab and you can mount and unmount using nautilus. To do all this I would open a terminal and gain superuser rights by saying "sudo -s". Start the editor by saying "gedit /etc/fstab". The angle brackets <> have to be ommited.

---

### Post by Endolith on 2007-11-09
> **hugmenot said:**
>  There is the a way to access Samba shares with Nautilus as you know (i.e., via GnomeVFS), but the actual apps have to support the method.

Ahh.

> With the next Gnome you will likely be able to use all apps, since they’ll switch to a better implementation of vfs.

But that will probably be a long time from now...

> Meanwhile you can learn how the traditional mounting is done. It’s also more efficient.

Why more efficient?

> Now your mount is properly listed in fstab and you can mount and unmount using nautilus. To do all this I would open a terminal and gain superuser rights by saying "sudo -s". Start the editor by saying "gedit /etc/fstab". The angle brackets <> have to be ommited.

Thank you for being detailed and not making assumptions about what I know.  :-)

---

