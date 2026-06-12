---
title: "Folder sharing problem on Hardy 64"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by mdewet on 2008-12-16
I tried to share a folder on hardy the 'right-click sharing options' way (I'm not yet clued up with the terminal).  All the necessary files were downloaded automatically, but I keep on receiving this error   

```

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

```

I am the only user on this computer, so I should have all the permission I need right?

( I also checked the "Allow other people to write in this folder" and the "Guest access" boxes in the File Manager GUI)

---

### Post by Iowan on 2008-12-16
One soluti0n I've seen involves adding yourself to the usershare group.  I'll try to find the link... [this]("http://ubuntuforums.org/showthread.php?t=1003144") thread is similar, but not the one I remember. [Another]("http://ubuntuforums.org/showthread.php?t=825965") similar thread - with possible solution.

---

