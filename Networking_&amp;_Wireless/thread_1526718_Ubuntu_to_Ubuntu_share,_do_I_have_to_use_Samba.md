---
title: "Ubuntu to Ubuntu share, do I have to use Samba?"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by Rubidot on 2010-07-08
I just want to share between Ubuntu machines; do I have to use samba?

---

### Post by endotherm on 2010-07-08
no, but it is the best option in many cases. i've never tried nfs, but I'm told it;'s a little dated.

one really simple way to do it if you don't have to preconfigure everything for unprivledged users, is to use the SCP protocol over ssh. takes about a minute to set up.

1) install ssh on the box you want to connect to (the "server")
```
sudo apt-get install openssh-server
```

2) on the client computer open nautilus, and hit Ctrl + L to enter location mode (so you can type in a path)
in the path bar, enter 
```

ssh://<servernameorip>/<Pathonserver>

```and hit enter. you will be prompted for login credentials, and then nautilus will show you the path on the server. if you don't provide a path, the window will default to / on the server box.

once you have it working one way, just do the same thing on the other box.

---

### Post by Iowan on 2010-07-08
Rather than repeat it, [here]("http://ubuntuforums.org/showpost.php?p=9016757&postcount=2") is a link to a post (mine) with links for NFS, SSHFS, and FTP. Hopefully one of them will be helpful.

---

