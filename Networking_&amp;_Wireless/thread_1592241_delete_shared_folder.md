---
title: "delete shared folder"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by hudo on 2010-10-10
Hello, 

where and how can I "delete" shared folder in lucid ?

In System-Administration->Shared Folder is non of my shared folder, so I cant delete them...

I can see those  shared folders with "Places->Network"  but I cant find out the path to the  folders, nor can I delete them.

---

### Post by Morbius1 on 2010-10-10
> In System-Administration->Shared Folder is non of my shared folder, so I cant delete them...There is to my knowledge no such path as System-Administration-Shared Folder.

There is a System-Administration-Samba however. Is it possible that you created your shares using Nautilus? If so your share definitions are not in smb.conf and will not show up in System-Administration-Samba.

Run the following command and see if it lists your "missing" shares:
```
net usershare info
```

---

### Post by KjellKod on 2010-11-19
Hi, 

I've the same problem. When I used "connect to server" -> "service type: Windows Share" I managed to get a typo and because I bookmarked it I cannot make it to go away. 

I.e. the "non-existing" share is always under "Places -> \\MyFailedShare" and I cannot remove it (nor use it of course)

---

### Post by KjellKod on 2010-11-19
Eeeh. Too long time to remove it made me overlook the obvious. 

I "bookmarked" it with "Places -> Connect to server",. but this is really just Nautilus so to remove it you start nautilus
Bookmarks -> Edit Bookmarks ->... just remove it and *voila*

.... :redface:

---

