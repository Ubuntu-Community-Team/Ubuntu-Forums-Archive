---
title: "Need Help with samba network shares."
date: 2012-03-23
forum: Networking &amp; Wireless
---

### Post by ChrisLancs on 2012-03-23
Hello, I am a linux newbie and i hope i provide the right information here in order to get this issue resolved, If i do not please feel free to ask for what you need to know.

My Setup:

Ubuntu 11.10 on a dual boot with windozy vista.
Samba is installed.

i have the following basic structure.

[LIST=1]
[*]Drive:[LIST=1]
[*]music
[*]video
[*]etc etc etc
[/LIST]

[*]Drive(ntfs file system):[list=1]
[*]websites
[*]misc files
[*]applications
[*]etc etc etc
[/list]
[/LIST]

Each of those primary directories has several (EG: music by artist, 100's) sub directories. I can share them without a problem if i want to do them one at a time and have hundreds if not thousands of mount points but that seems highly impractical and inefficient to me.

Finally i get to my point, is it possible to share just a main directory and have all of the subdirectories & files within available to access.

Currently i seem to be missing something and i can share a single directory, and all "files" inside that do share and i can open them.

The first layer of subdirectories are visible over the network but i cannot access them i get a message stating unable to mount. so anything inside those, be it another sub, or any sort of file in inaccessible over my network.

---

### Post by wyliecoyoteuk on 2012-03-23
You can only mount a share,not a subdirectory within it.
You should be able to browse and access subdirectories within a share, *as long as they are set to inherit permissions* from the share's root directory, and your samba user has the right permissions.

Samba users and Linux users are separate unless you map between them.

Also, sharing a directory from an NTFS file system via Samba and Linux is not ideal.
NTFS and Linux filesystems do not have a common permissions structure.

---

### Post by ChrisLancs on 2012-03-23
> **wyliecoyoteuk said:**
> You can only mount a share,not a subdirectory within it.
You should be able to browse and access subdirectories within a share, *as long as they are set to inherit permissions* from the share's root directory, and your samba user has the right permissions.

Samba users and Linux users are separate unless you map between them.

Also, sharing a directory from an NTFS file system via Samba and Linux is not ideal.
NTFS and Linux filesystems do not have a common permissions structure.

Thank you for the info, it must be a permissions issue in that case. i will look into it, i might then have to chmod -r the directory?

I recall reading something on this though that recursing the permissions doesnt work as expected. EG, everything would end up with the same permissions as files and directories are not separately distinguished. i must have something set up wrong somewhere.

---

### Post by wyliecoyoteuk on 2012-03-23
You can map Samba users to Linux users.
Not knowing how you are managing Samba doesn't help.
Some of the GUI solutions can be a little flaky.
SWAT or WebMin are probably the best,both are web based.
Webmin is nice and easy to understand, and it is useful for other things too.

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html)

[http://www.webmin.com/](http://www.webmin.com/)

---

### Post by Morbius1 on 2012-03-23
>  Finally i get to my point, is it possible to share just a main directory  and have all of the subdirectories & files within available to  access.
Yes

As for you inability to achieve that by creating a share of the parent directory we need to know how you created the samba share. There are 2 methods so there are 2 ways to provide that answer.

Please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

