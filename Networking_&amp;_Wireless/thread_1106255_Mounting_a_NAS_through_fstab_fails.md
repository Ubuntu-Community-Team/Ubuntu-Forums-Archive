---
title: "Mounting a NAS through fstab fails"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by w.hellinga on 2009-03-25
Dear friends,

I fail trying to mount with curlftpfs a NAS through /etc/fstab. It can only be done when typing in a termina "sudo mount -a". All maps are mounted well then an visible on the desktop.

**fstab:**
curlftpfs#192.168.1.31/iedereen /home/willem/IedereenOpNetwerk fuse rw,allow_other,auto,user 0 0
curlftpfs#192.168.1.31/muziek /home/willem/MuziekOpNetwerk fuse ro,allow_other,auto,user 0 0
curlftpfs#192.168.1.31/foto /home/willem/FotoOpNetwerk fuse ro,allow_other,auto,user 0 0
curlftpfs#192.168.1.31/willem /home/willem/WillemOpNetwerk fuse rw,allow_other,auto,user 0 0

**/root/.netrc:**
machine 192.168.1.31
login willem
password [geheim natuurlijk]

All necessary maps are present in /home/willem.

I got lost completely, so please help me solve this thing and make it possible to step on to the next release, it's still *Hardy* :( here...

Lots of thanks

Sincerely

---

### Post by Iowan on 2009-03-25
> **w.hellinga said:**
> I got lost completely, so please help me solve this thing and make it possible to step on to the next release, it's still *Hardy* :( here...
Still Gutsy here - so I'm running short on time/support...
Have you seen [this]("http://ubuntuforums.org/showthread.php?&t=283131") fstab How-To?
I know nearly nothing about curlftpfs, but found [this]("http://ubuntuforums.org/showthread.php?t=441126") How-To.

---

