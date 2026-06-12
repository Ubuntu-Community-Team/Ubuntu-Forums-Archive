---
title: "Can't share folder"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by winhaung on 2010-03-18
'net usershare' returned error 255: net usershare add: cannot share path /media/New Volume/movie as we are restricted to only sharing directories we own.
    Ask the administrator to add the line "usershare owner only = False" 
    to the [global] section of the smb.conf to allow this.

I got above error when I try to share a folder of other harddisk. What can  i do?

---

### Post by winhaung on 2010-03-19
Now it solved!
typing
gksu gedit /etc/samba/smb.conf
in terminal window
and adding line "usershare owner only = False" in global section
definitely solved my 'sharing folder' problem
Thank you a lot!

get from [http://ubuntuforums.org/showthread.php?t=958457](http://ubuntuforums.org/showthread.php?t=958457)

---

### Post by Bucky Ball on 2010-03-19
It tells you to do that right there in the original error message!

> ... add the line "usershare owner only = False" 
    to the [global] section of the smb.conf to allow this.

Please mark thread as 'solved' from 'Thread Tools' to assist others. ;)

---

### Post by PhoenixDream on 2010-05-30
I get the same error msg and added "usershare owner only = False" and it rejected it again when I attempted to create a share. I added the line at the very bottom of the conf file.

Have followed the link above from another post. Can share folders under my home directory but not from my secondary hard drive.

---

