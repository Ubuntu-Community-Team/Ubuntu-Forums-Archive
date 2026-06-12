---
title: "unable to view windows network"
date: 2012-10-14
forum: Networking &amp; Wireless
---

### Post by T31337 on 2012-10-14
When I Open Network > Windows Network i get an error unable to mount location "Failed to retrieve share list from server" 

yes my windows 7 is running on same workgroup. My homegroup does have password protected sharing enabled in windows7 
i also have ufw enabled to allow samba service in and out. Also I can run "nautilus smb://*.*.*.*/" and access the shared files :confused:

---

### Post by T31337 on 2012-10-23
Solved :)

---

### Post by scania_gti on 2012-10-23
But how? :confused:

---

### Post by T31337 on 2012-10-25
I am not 100% sure how, The problem resolved it self I loged in as root and attempted to view netowk and that worked so i loged back in as me and went to network and i was able to view the network with no problems....

---

### Post by T31337 on 2012-10-26
okay, now I get that same error while trying to browse the network again but I can see My shared Folders In The Main Network Window, But I Am unable To browse the windows network :(

---

### Post by Rezliw on 2012-10-27
Having similar problem:  From terminal  smbtree shows everything on windows network but can not access through file or locate.  Can not mount error with network browse.

Arrrrrrrgh!

---

### Post by T31337 on 2012-10-27
I can now browse the windows network but when I try to connect to any machine other than my own I get error could not retrieve file share list from server but using command smb://(ip address) I can provide the login credentials and view shared files...

---

