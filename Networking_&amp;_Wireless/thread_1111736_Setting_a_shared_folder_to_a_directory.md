---
title: "Setting a shared folder to a directory"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by dragonfellow17 on 2009-03-30
How do you make a shared folder mounted to a folder? I need to do this to play music and movies in Banshee and in VLC Totem etc. I keep searching but I can't find anything maybe because I'm not using the right terminology. There was a terminal command that I used in openSUSE but I lost it. I would also like to make it automatic connect so I don't have to put the command in every restart.

---

### Post by sinclair86 on 2009-03-31
Are you talking about making a link (shortcut). "shared folder mounted to a folder" ? Little confused on what you are saying.

---

### Post by dragonfellow17 on 2009-03-31
I want to put smb://192.168.0.108/External into /home/ryan/External

---

### Post by coutts99 on 2009-03-31
> **dragonfellow17 said:**
> I want to put smb://192.168.0.108/External into /home/ryan/External


```
mount -t cifs -o username=server_user,password=server_password
//192.168.0.108/External /home/ryan/External
```

To add to /etc/fstab -:

```
//192.168.0.108/External /home/ryan/External cifs file_mode=0770,dir_mode=0770,uid=1000,username=server_user,password=server_password,domain=server_domain,noperm 0 0
```

---

### Post by sinclair86 on 2009-03-31
fudge nvm he beat me to it

---

### Post by dragonfellow17 on 2009-03-31
lol I just came back from school and turned my computer on and it was already mounted in home so I guess I did fstab right.

---

