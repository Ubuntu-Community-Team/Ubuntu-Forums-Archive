---
title: "Network name"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by Himself2007 on 2009-11-03
[B][I][COLOR="DarkGreen"]Hello


About my network.
I installed Ubuntu 9.10 and found that other Windows XP computers on my network are accessible from Ubuntu.
Good!
I installed Samba, and configured a new user.
But Samba is not included in my present Windows network but created its own network called "workgroup" in Ubuntu.
But I confirmed I can use any Windows computers to access this "workgroup" network in Ubuntu.
So right now, I'm perfectl bi-directional but using two different network names.
Question : how can I unify these two networks together?
I would like to include Ubuntu's "workgroup" network into my present network so I can deal with only one network name.

Himself2007[/COLOR][/I][/B]

---

### Post by Iowan on 2009-11-03
Edit the */etc/samba/smb.conf* file. There is a line ```
workgroup=???
``` (I presume yours is "workgroup") change that to the name of your Windows workgroup...
Might need to use:```
sudo nano /etc/samba/smb.conf
``` or```
gksudo gedit /etc/samba/smb.conf
```

BTW, from the Code of Conduct:> # Please use color and font properties for highlighting portions of your text, and not for all of the text in your post.


---

### Post by Himself2007 on 2009-11-04
iowan

Thanks for the good advices.
And sorry for the highlighting...I didn't know.
Thanks

Himself

---

