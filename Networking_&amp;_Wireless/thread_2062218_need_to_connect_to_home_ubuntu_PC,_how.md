---
title: "need to connect to home ubuntu PC, how?"
date: 2012-09-24
forum: Networking &amp; Wireless
---

### Post by gychang on 2012-09-24
I have latest lubuntu install, works well (PC-A).  I need to share folders on my 12.04 ubuntu PC (PC-B).  All part of home network connected with wireless.

is there a newbie guide on how to share folders and install/configure samba so I can d/l files from my ubuntu PC (PC-B) to my lubuntu machine (PC-A)?

thanks,

---

### Post by nothingspecial on 2012-09-24
If it's ubuntu and lubuntu you don't really need samba.

On PCB ```
sudo apt-get install openssh-server
```

On PCA ```
ssh-keygen
ssh-copy-id user@ipaddress
```

eg ```
ssh-copy-id bob@192.168.0.5
```

Type the password of PCB when prompted.

Then on PCA open pcmanfm (the file browser) and in the address bar at the top put ```
sftp://bob@192.168.0.5/
```

or whatever the actual user and ip are. Then add a bookmark using the bookmark menu. Now you will have full access to PCB from PCA

---

