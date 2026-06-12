---
title: "Failed cifs mount left icon on desktop"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by volkerw on 2010-09-25
p { margin-bottom: 0.08in; }  Hi,

looking for advice. Using Nautilus I tried to open (mount) a share on my Windows server. Always worked and still works perfect. One attempt failed and left an icon on the desktop where usually the share (mount point) would show up. The icon title says:
*stuff* on myserver.volume.
stuff is the share name and myserver is the server name. I cannot remove the icon. The type is unknown. When I try to mount *stuff* (my network share) again, I get tons of Nautilus icons in the bottom panel of the desktop. It goes on and on until I reboot or log off. Mounting the cifs share via terminal and mount command fails with 



mount: wrong fs type, bad option, bad superblock on //theakirk/iso,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Any help in getting this fixed is appreciated. Currently I don't even know where to look.

---

### Post by dmizer on 2010-09-26
I'm not sure how the system places the links, so please post the output of:
```
ls -la Desktop/
```

> **volkerw said:**
> Mounting the cifs share via terminal and mount command fails with 



mount: wrong fs type, bad option, bad superblock on //theakirk/iso,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Any help in getting this fixed is appreciated. Currently I don't even know where to look.
To fix this, please run this command:
```
sudo apt-get install smbfs
```

---

### Post by volkerw on 2010-09-26
Yup. Worked. I was able to remove the mount and the icon disappeared from the desktop. 
Thanks dmizer.

---

