---
title: "Possible to change permissions via FTP?"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by Igniteflow on 2009-03-30
Sorry if this is a noobish question, but I am editing a web site logging in through

Places > Connect to Server

and editing the pages with the text editor.  I need to change some of the file and folder permissions. Is it possible to do this via FTP with Nautilus or would I need to SSH in via the terminal?

---

### Post by KCG102282 on 2009-03-30
I am not sure if you could with Nautilus as I have never used it as an FTP program, but you can do it with Filezilla. ```
sudo apt-get install filezilla
```

---

### Post by Iowan on 2009-03-30
Just my opinion, but I prefer the security of SSH.

---

### Post by Igniteflow on 2009-03-31
Filezilla works great thanks!  I just figured out SSH login too, so will probably just use FTP for uploading files to the site now and SSH for editing php/html etc so cheers for the tip Iowan

---

