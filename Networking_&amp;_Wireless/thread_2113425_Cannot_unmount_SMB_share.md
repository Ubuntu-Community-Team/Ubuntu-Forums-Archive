---
title: "Cannot unmount SMB share"
date: 2013-02-07
forum: Networking &amp; Wireless
---

### Post by flyingfisch on 2013-02-07
I have setup file sharing with nautilus over a lan using samba. It works fine but when I try to unmount the shared folder (by right-clicking in nautilus and pressing unmount on the client system), I get an error message that says 

```

Unable to unmount location
Operation not supported by backend

```

Any ideas on what's happening here?

---

### Post by PowerBarry43 on 2013-02-07
Hi

What happens if you try to unmount from a terminal

```
umount /path/to/share
```

to me this smells like a permissions problem, if you have to run:

```
sudo umount /path/to/share
```

then it's because you're user doesn't have rights to unmount the share

Hope this helps!

Barry

---

### Post by flyingfisch on 2013-02-07
Here's the outputs:
```

flyingfisch@Office-OptiPlex-745:~$ umount smb://192.168.143.241/media-old-comp/
umount: smb://192.168.143.241/media-old-comp/ is not mounted (according to mtab)

```I ran sudo umount just for the heck of it:
```

flyingfisch@Office-OptiPlex-745:~$ sudo umount smb://192.168.143.241/media-old-comp/
umount: smb://192.168.143.241/media-old-comp/: not found

```Am I doing it wrong?

EDIT:

Works now. If I go to *smb://192.168.143.241* with nautilus and try to unmount the shares, i get the error. However, if I press the umount symbol in the sidebar it works. weird.

---

