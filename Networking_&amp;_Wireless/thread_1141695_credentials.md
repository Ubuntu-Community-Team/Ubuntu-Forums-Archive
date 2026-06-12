---
title: "credentials"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by theozzlives on 2009-04-28
I'm trying to mount some shares in my fstab, I have to put my password in there and I don't like that. I figured I'd use a credentials file in my home but it don't work. Here's how I'm mounting:

```
//192.168.1.3/pictures /home/ozzie/Pictures cifs credentials=/home/ozzie/.creds 0 0

```

my .creds file:

```

username=myname
password=mypassword

```

What am I doing wrong?

---

### Post by Iowan on 2009-04-28
Perhaps you've already seen [this]("http://ubuntuforums.org/showthread.php?&t=283131") **fstab** How-To. > **bodhi.zazen said:**
> ...
//Server/share /mnt/samba cifs users,auto,credentials=/path/credentials_file,noexec 0 0
...

---

