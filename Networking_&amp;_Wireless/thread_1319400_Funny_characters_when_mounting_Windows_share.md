---
title: "Funny characters when mounting Windows share"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by bovender on 2009-11-08
Hi all,

I am trying to mount a Windows share in a terminal. It works perfectly well using Nautilus, but I get strange character problems in the terminal.

This is the command that I use to mount:
```
sudo mount -t cifs //server/users/mylogin mountpoint -o username=mylogin,domain=ourdomain,iocharset=utf8,file_mode=0777,dir_mode=0777

```

It mounts alright, but when I do dir -l I get this:

```
d????????? ? ? ? ?                ? periments
```

This is a folder on the Windows share whose correct name is "Experiments". I notice that the first two letters are missing from every single file and folder in the mounted share, and all the permissions are replaced with question marks, as above.

I have attempted the following, all without success:
[LIST]
[*]Change "cifs" to "smbfs"
[*]Remove "iocharset=utf8"
[*]Leave out the "file_mode" and "dir_mode" parameters
[/LIST]

What can I do to get the appropriate display of file and folder names? Again, it works perfectly well in Nautilus.

Thanks!

---

