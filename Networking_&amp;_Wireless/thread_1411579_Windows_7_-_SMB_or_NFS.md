---
title: "Windows 7 - SMB or NFS?"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by kfuglsang on 2010-02-20
Hi all,

I will next week be receiving my Zotac ION hardware which I plan to install Ubuntu Karmic on. I have a gigabit ethernet at home and a few Windows 7 Pro machines.

I would like to be able to mount network shares from the Ubuntu machine on my Windows 7 clients.
Question is, which will yield the better performance? SMB or NFS? I noticed that the latest Samba versions supports an experimental SMBv2.
It's been several years since I've used linux the last time, so I haven't really followed discussions nor have I been able to find any recent comparisons of the performance.

Best regards
Kenneth
Denmark

---

### Post by Jose Catre-Vandis on 2010-02-20
If (and thats a big if) you can get nfs working use NFS, but as your network appears to be mostly Windows machines, I suggest you set up samba to serve up shared folders/files. A good howto comes from [stormbringer]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba") on the forum

---

### Post by kfuglsang on 2010-02-20
Thank you for your reply.

I just realized that the NFS client in Windows 7 is not even available in the Professional edition. It is only available in Enterprise and Ultimate.

Samba it is then :-)

---

