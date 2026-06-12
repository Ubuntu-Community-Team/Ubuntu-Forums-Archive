---
title: "Fast CLI File Transfer Solution w/ Time Preservation?"
date: 2011-03-04
forum: Networking &amp; Wireless
---

### Post by clevertomato on 2011-03-04
I use basic ssh and scp on a regular basis and sometimes for file transfer... certainly over public networks. However, often I want to transfer large (several GB) files from one place on my LAN to another.

I've read that FTP is the fastest, and when I'm transfering many GB, fast matters. Of course I know it's not secure, but I don't need security on my home wired LAN. What I do need many times is preservation of date and time of each file when uploading. Filezilla does that and I use it, but sometimes I need a CLI solution. I have use ncFTP and been happy with it until I realized it doesn't preserve date and time on uploads (probably not on downloads either, haven't looked).

Is there a CLI FTP solution out there that will preserve file date and time information on file transfers (including uploads)?

---

### Post by gmargo on 2011-03-04
How about **sftp(1)** or **rsync(1)**?

---

### Post by clevertomato on 2011-03-25
I've read sftp can be even slower than scp. Anything encrypted is going to take longer than unencrypted, and I don't need encryption for my LAN. Rsync... I don't know anything about it's speed.

---

### Post by Metallion on 2011-03-25
I really like lftp myself. Not sure if it preserves date/time though.

---

