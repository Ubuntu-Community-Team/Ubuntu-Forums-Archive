---
title: "Samba and &quot;No space left on the device&quot;"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by NexusGS on 2009-10-31
Hi all...I am really confused and even though I googled it many times, I still need your help on that...

I am using Ubuntu 9.04 64-bit version. Everything works sooo great...I only have 1 issue: I have a Samba Server on my LAN that is running FreeBSD and is running Samba version 3+. But, when I copy a file larger than 2GB, when I copy files larger than 2GB, when copy should finish, I get an error message "No space left on the device". I have tried both smbfs and cifs as filesystem on fstab...I also used lfs as option.

My fstab line:
```
//192.168.1.101/* /mnt/* smbfs guest,noperm,rw,lfs,iocharset=utf8,file_mode=0777,dir_mode=0777,lfs 0 0
```

My Samba share is free for all...

Any thoughts guys? I am stuck in a way with...

---

### Post by headvampyre@hotmail.co.uk on 2009-10-31
How big is your Hard-Drive and how much space is left cos i had this error when i accidently assigned 500 meg to /home

---

### Post by NexusGS on 2009-11-01
It's a 500GB disk that has 350GB free space...And I am not talking about a local filesystem...It's remote via samba...

---

### Post by headvampyre@hotmail.co.uk on 2009-11-01
im sure samba had probs with files that large as i heard about them on net also have you assigned a partition to /home cos if you do that that could be the prob

---

### Post by NexusGS on 2009-11-01
No I don't have partition assigned to /home. And I had the samba server at the past using Slack 10 and had no problem on large files...

---

### Post by headvampyre@hotmail.co.uk on 2009-11-01
what vers of samba r u on

---

### Post by NexusGS on 2009-11-01
Samba version 3.0.36

---

### Post by NexusGS on 2009-11-02
Any idea??

---

