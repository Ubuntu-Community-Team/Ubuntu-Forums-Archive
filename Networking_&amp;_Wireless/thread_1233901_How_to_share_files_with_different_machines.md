---
title: "How to share files with different machines"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by codingfreak on 2009-08-07
Hi

I like to know how to share some PDF files in my linux server with all users in the network. Any way which is as simple as we do in a windows system.

---

### Post by snek on 2009-08-07
I think so, just right click a folder and select Sharing Options.
I am using Ubuntu Jaunty though, and have Samba installed.. Normally the way to do this is by using Samba, so you might have to install that first before you can access this option.

---

### Post by howefield on 2009-08-07
Do you have a gui on your server or are you running with the command line ?

---

### Post by codingfreak on 2009-08-07
I do have the GUI ....

Seems I should install SAMBA first

---

### Post by shredder12 on 2009-08-07
well there is another simple way...
set up a ftp server...
try vsftpd it works great for me..
 ```
sudo apt-get install vsftpd
```

after the installation there will be a folder created in your Home directory by the name of "ftp"
whatever you put in that folder with proper permissions will be visible on your ftp server

---

### Post by codingfreak on 2009-08-07
I have successfully installed samba and the service is UP and running

Now tell how can I make users from a WINDOWS machine to access a shared directory on my Linux Server.

---

### Post by codingfreak on 2009-08-07
> **shredder12 said:**
> well there is another simple way...
set up a ftp server...
try vsftpd it works great for me..
 ```
sudo apt-get install vsftpd
```after the installation there will be a folder created in your Home directory by the name of "ftp"
whatever you put in that folder with proper permissions will be visible on your ftp server

But I think every user should give the username and password to access your FTP folder ??? Isn't there any way as we share in WINDOWS??

---

### Post by shredder12 on 2009-08-07
> **codingfreak said:**
> But I think every user should give the username and password to access your FTP folder ??? Isn't there any way as we share in WINDOWS??


no that's not necessary.. by default.. anonymous users will be allowed access...

---

### Post by garikaib on 2009-08-07
Vfsftpd is the way to go! Samba can be jerky especially when accessing Windows shares from Ubuntu. My guess the guys at Microsoft have some undocumented calls in their code!

---

### Post by codingfreak on 2009-08-07
Thank you guys .... VSFTPD I am able to do it easily.

But a doubt .... How does the Samba way of implementation differs ????

---

### Post by codingfreak on 2009-08-09
Seems SAMBA style of implementation is not really easy and straight forward ???

---

### Post by snek on 2009-08-10
Samba can be a bit of a b**** to setup, yeah :)
If you want I can share a config which allows anonymous sharing which rewrites all users to a single user. Thus generating a "public" share.

---

