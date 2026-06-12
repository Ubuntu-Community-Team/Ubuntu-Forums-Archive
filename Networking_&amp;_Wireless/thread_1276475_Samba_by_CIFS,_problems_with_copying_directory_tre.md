---
title: "Samba by CIFS, problems with copying directory tree"
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by amorfis on 2009-09-27
Hi,

I have server with samba share, which is mounted by CIFS on my client machine under /media/share.

/media/share ownership is root:samba, and my user also is member of group samba. In smb.conf on server I have:

```

force create mode = 0664
force directory mode = 2775
force security mode = 0664
force directory security mode = 2775
```
So /media/share directory has rights drwxrwxr-x. Every file that I create in this directory has rights rw-rw-r--

I can create directory. I can create file. I can go into created directory and create file there.

I can't copy directory tree. When I issue:

```

cp -r /home/frank/photos/Tymek/ /media/photos
```
Directory "Tymek" is created, but no files inside. I get messages like

cp: cannot create regular file `/media/photos/Tymek/usg_10.bmp': Permission denied
Even if I can go into Tymek directory and create file without any problem.

Such command works:

```

cp -r /home/frank/photos/Tymek/ /media/photos/
```
(slash at the end added)

But Nautilus seems to use first method, it has problems copying whole directories, and I need it.

---

