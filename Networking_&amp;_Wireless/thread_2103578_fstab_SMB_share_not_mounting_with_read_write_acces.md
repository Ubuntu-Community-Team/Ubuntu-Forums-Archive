---
title: "fstab SMB share not mounting with read write access to Windows 8 machine"
date: 2013-01-10
forum: Networking &amp; Wireless
---

### Post by sizzlefire on 2013-01-10
I am using windows 8 and Ubuntu 12.10 and the windows 8 machine is setup as a SMB share. I have read through the man page for cifs-mount, but now matter what I try, I cannot get the share to give me read and write access to the server. Ubuntu will not let me install smbfs as it is obsoleted, so I am unsure where to go from here. The command I am using is

```
//theip/Users /media/folder cifs domain=domain,username=user,password=secret,uid=me,rw
```

Thank you!

---

### Post by sizzlefire on 2013-01-13
I must've been very tired when I was dealing with this. I just checked again and the command seemed to work fine when I changed it to

```

//theip/Users /media/folder cifs domain=domain,username=me,password=mypass,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0

```

I found this on this page: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

