---
title: "UBUNTU Server + WINDOWS VISTA &amp; 7 LOCAL BOXes BACKUP"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by etail907 on 2010-07-15
HI All

Need some advice

What is the best solution to backup few windows vista & 7 boxes from LAN on to ubuntu server(based in same LAN)

Thx

SI

---

### Post by cj.surrusco on 2010-07-15
> **etail907 said:**
> HI All

Need some advice

What is the best solution to backup few windows vista & 7 boxes from LAN on to ubuntu server(based in same LAN)

Thx

SI

What are you looking to backup? An entire image, the My Documents folder?

---

### Post by etail907 on 2010-07-15
hi cj

mainly documents & settings folder :)

users in my company put their stuff on the desktop :-/

thx

si

---

### Post by cj.surrusco on 2010-07-15
I would suggest an FTP server. They allow sharing files regardless of the file system, so you don't need to worry about Windows not recognizing the Ubuntu server's file systems. 

I use vsftpd to manage my FTP server. Check out the HOW-TO [here]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html").

---

### Post by etail907 on 2010-07-16
Hi

Hmmmm 

I know how install it but what is the policy to use it.

What is the data(backup flow): 

server will pull all data from lan machines 

or lan machines will send data do server 

??

---

### Post by cj.surrusco on 2010-07-16
You would be able to upload data to the FTP server to back it up.

---

### Post by etail907 on 2010-07-17
HI

Yeah but i need a script that will do it in schedule - like cron job

---

### Post by cj.surrusco on 2010-07-19
You can use [CurlFtpFs]("http://curlftpfs.sourceforge.net/") to mount the FTP server as a normal file system and then set cron to run a command to copy the files to the FTP server.

---

