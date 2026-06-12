---
title: "connecting to win2k3 server"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by vieira on 2006-06-13
Hi, I am still quite new to Linux and have been working with Kubuntu 5.10 to write my dissertation. This requires me to be connected to a win2k3 server to access network drives.
After a lot of trial and error I managed to connect to the server. However, a couple of days ago, I upgraded to Kubuntu 6.06 and since then I have not been able to set things up the way they used to be. I guess I learned to never change a running system the hard way... :-( 
I have followed variuos faqs and how-tos and have managed to set up samba and kerberos. I can connect to the server using the smbclient command via the console. However, I cannot connect using smb4k as I used to. This is necessary for me, as I am not skilled enough to work via the console. I need some gui to work with the folders. I would be happy to post the links of the web pages I have used or any information regarding the files I have edited. I just don't know which the crucial ones are. As I said, I am a newbie...

I would greatly appreciate any help as I am desperate to continue working on my dissertation.

Thank you!

---

### Post by Ctrl+Alt+Del on 2006-06-13
You could try mounting your your network share directly which is imo the smartest way as it allows unrestricted usage.
put sth like that in your /etc/fstab
```
//servername or ip/share  /mnt/share  cifs  user=yourusername,password=yeahright,user,rw,noauto  0  0
```

---

