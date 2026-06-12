---
title: "ubuntu 10.04 can't access windows share"
date: 2011-02-11
forum: Networking &amp; Wireless
---

### Post by dsula on 2011-02-11
Hi,

I have the following network setup:
1. windows 7 (native)
2. windows vista (in vmware)
3. 4x windows xp (3 native, 1 in vmware) 
4. 3x ubuntu x64 10.04 (1 native, 1 in virtualbox, 1 in vmware)
5. 1x ubuntu x32 10.04 (native)

Two ubuntu are samba file servers.
All windows share some folders.

ALL windows machines can access ALL other shared folders on ANY machine, ubuntu, any windows, anywhere, no problems.

However the ubuntu machines can rarly access anything. Sometimes, on a lucky day, I can access some of the XP machines, however painfully slow (intial mount is slow, later file access is ok). However ubuntu can never access the samba shares on the server, it can't access vista, however it can sometimes see the shared folders of Windows 7. However trying to access them will then lead to a mounting error.

I'm at a loss, totally. Especially because ubuntu can't even access samba shares running on ubuntu? What could that be? Also I remember times when this all was working. However after several updates (both ubuntu and windows) all of a sudden it wouldn't work anymore. When that happened I don't know, because I rarely use ubuntu clients and therefore didn't notice immediately,

Any help is appreciated.

---

### Post by headvampyre@hotmail.co.uk on 2011-02-11
If your planning on sharing files from Linux aswell - try Samba4 ( wiki.samba.org/index.php/Samba4/HOWTO ), its not finished yet, so dont expect it to be completely stable, but make sure you remove samba and smbclient, but symlink the samba4 smb client into /usr/sbin
ln -s /usr/local/samba/bin/smbclient /usr/sbin

i find this version of smbclient much better than the default ubuntu ones :)

---

