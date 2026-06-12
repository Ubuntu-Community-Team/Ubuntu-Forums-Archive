---
title: "bulk renaming files on an SMB share"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by Keith_Beef on 2011-01-23
I have a Netgear ReadyNAS NV in the basement, that I want to use to serve up video files over my network to a TV in the living room.

Now, I have a lot of files that HandBrake encoded and it gave the files an m4v suffix. Even when the files are in a codec that the TV can handle, it refuses to load them because of this suffix... so I want to rename them all.

This is fairly simple for files on a local filesystem. I can simply cd into the directory containing the files, and do something like the commands below.

```
$ for a in `ls`;
> do
> stem=`echo ${a} | cut -f1 -d"."` ;
> mv ${a} ${stem}.mpg ;
> done
```

But the files in the NAS are shared by SMB... and I can't simply do this:
```

$ cd smb://192.168.0.4/media/Films/
```

It doesn't work.

Although there are a few smb commands available (smbstatus, smbget, etc.), I've not found any commands like smbls or smbmv.

Are there any special commands or utilities around that can do the kind of thing I'm trying to do?

K.

---

### Post by dandnsmith on 2011-01-23
Have you tried using smbmount to mount the filesystem locally, and then doing it as a normal operation as you posted above?

---

