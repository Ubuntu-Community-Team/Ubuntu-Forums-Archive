---
title: "automount nfs only with a particular net"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by zip5987 on 2009-12-25
Hello everyone and merry xmas.
I have just installed ubuntu 9.10 and it's very nice: i would like to use it. I come from 2 years of Gentoo, Ubuntu is amazing simple: it saves me time.

I would like that it can automount a particular nfs share only when i attach to a particular net (e.g. my home server has a nfs share, so i want to automount it when i attach to my home wlan). Is it possible to do so with GUI of distribution? I would not like to edit by hand files like /etc/fstab: i would like a tool that can do all automatically. 

I imagine a tool with options like this:

"Do something when you connect to this net" -> "Mount a remote share" -> "NFS" -> "Select server, select mountpoint"

and

"Do something when you disconnect to this net" -> "Unmount a remote share"

Is there something like that?
Thank you very much
Goodbye

---

### Post by ant2ne on 2009-12-25
i think you are looking for something like this, but different.
```
pingtest.sc
#!/bin/sh
# if file exists (some network share) = yes exits 
# if file exists (some network share) = no then pingtest.sc
# if pingtest = fail then exit
# if pingtest = win then mount
clear
PingFail()
{
echo Worked!!!
}
ping -c 1 192.168.1.1 && PingFail
```I had modified this script so it did something similar, but I lost the modified version. But this should be enough to build on it.

---

