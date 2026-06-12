---
title: "Connecting to Windows Share"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by Skavenger0 on 2010-11-23
I'm a little stuck and I hope someone can help.

I'm configuring Ubuntu 10.04 x86 to work with a windows domain with multiple users.

All users need a specific network share mapped.
I am using Likewise Open to join the domain at the moment.

This is what I've got so far.

```
mkdir -p /media/S
chmod 777 /media/S

Added the following line to /etc/fstab
//[SERVER]/[SHARE] /media/S cifs username=[USERNAME],password=[PASSWORD],iocharset=utf8,codepage=unicode,unicode 0 0
```

This works fine so long as I  specify the username and password statically. Is there a way I can get it to mount using the currently logged in users credentials so that it mounts automatically?

The other issue then is how to I specify that user is allowed read and write access?

I've tried googleing and found very little information.

---

### Post by Skavenger0 on 2010-11-23
Ok Problem 2 Solved by adding "fmask=666,dmask=777" apparently.

```
mkdir -p /media/S
chmod 777 /media/S

Added the following line to /etc/fstab
//[SERVER]/[SHARE] /media/S cifs username=[USERNAME],password=[PASSWORD],iocharset=utf8,codepage=unicode,unicode,fmask=666,dmask=777 0 0
```

Is it possible to create a script at startup that catches the domain username and password and saves it to a file like ~/.pass which is only readable by root then use "credentials=~/.pass" in fstab?

---

### Post by Skavenger0 on 2010-11-25
Bump

---

### Post by Skavenger0 on 2010-12-01
Anyone, any ideas?

---

