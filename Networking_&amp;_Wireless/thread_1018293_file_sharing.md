---
title: "file sharing"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by chrisr6 on 2008-12-21
I have a little problem here i currently have my xbox 360 connected directly via ethernet crossover to my computer which is running single operating system of ubuntu 8.10. I have it set up to share my computers wireless internet connection and that is working great but now i would like to be able to share my music and movies if anyone has had succes with this and could lend me a hand it would be appreciated.

---

### Post by DieB on 2008-12-22
did u try it with right-click on the folders and choose sharing-options (might be named a bit different, but the sign is a folder with a pipe going out. here take care u allow guests.

hope it was a help

---

### Post by chrisr6 on 2008-12-22
yes i have done this but the xbox does not find the computer

---

### Post by DieB on 2008-12-22
I#m sorry for not having a  xbox, but at what domain is your xbox lookin workgroup or domain or mshome(which is what ubuntu uses)?

to change the workgroup in ubuntu type following in aterminal:

sudo gedit /etc/samba/smb.conf

scroll down a bit and it there offers you to change the domain, also i would recommend making your machine a winsserver.

---

### Post by chrisr6 on 2008-12-24
I have had no luck Does any one no is it possible to share video and media via ethernet using ubunbtu 8.10

---

### Post by compgeek83 on 2008-12-25
on the xbox is there any way to browse by ip address?  if so just type in your linux box'x IP address

---

### Post by Iowan on 2008-12-26
> **chrisr6 said:**
> I have had no luck Does any one no is it possible to share video and media via ethernet using ubunbtu 8.10It's possible.  You'll need to set up the "server" to share - either NFS, Samba, SSHFS, or something else. How-To's listed [here]("http://ubuntuforums.org/showthread.php?t=1009962") (post #2).

---

