---
title: "can't mount a network drive"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by archik1989 on 2010-07-28
Hi all!

I know that you're gonna kill me for this post, but I really don't know what is going on.

so, here it is:

```
 $ sudo mount //192.168.1.17/freespace /mnt/storage/
mount: wrong fs type, bad option, bad superblock on //192.168.1.17/freespace,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
 
```any help?

also, when i do this:

ALT+F2>> smb://192.168.1.17/freespace it WORKS!!!

I would like to know as well about how to see mounted properties about mounted devices/folders which done by ALT+F2 command.....I mean I would like to see with what conf it runs out? how does it detect File system, and why it does support Russian language in files...I remember when I did it before in fstab I had to write iocharset=utf8 to see russian named files.

---

### Post by archik1989 on 2010-07-28
ok....i a little figured out that package smbfs wasn't installed.

i installed it and I could it mount by the console 

```

sudo mount //192.168.1.17/freespace /mnt/test

```

but in fstab i write

```

//192.168.1.17/freespace /mnt/test auto   defaults,iocharset=utf8 0 0

```

it doesn't work!

it says 

```


mount: special device //192.168.1.17/ does not exist


```

---

### Post by archik1989 on 2010-07-28
i'm really sorry....

now i figured 

i typed

//192.168.1.17/freespace /mnt/test cifs defaults 0 0 

and 
 sudo mount -a has worked!!!!

but......still....i'm trying to remember how to enable to display russian named folders and files(((((( still can't get it worked..

what kind of configuration should i write in fstab to get it worked???

---

### Post by archik1989 on 2010-07-28
ok....now i got russian language worked...

```


//192.168.1.17/Freespace        /mnt/storage    cifs    defaults,iocharset=utf8,codepage=cp866   0 0


```

but why I can't do any changes in this folder??

why it needs a password when i mount it? there is no pass on serv...
it works only if i type any password...so what is the mount option to boot it without password?

and when my laptop is booting i takes some more time because i saw some errors while booting something that says failed on mouting cifs.....why??

i don't want to wait more second for booting my system

---

