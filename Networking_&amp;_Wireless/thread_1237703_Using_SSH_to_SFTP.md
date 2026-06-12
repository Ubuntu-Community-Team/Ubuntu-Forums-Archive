---
title: "Using SSH to SFTP"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by x_jose_x on 2009-08-11
Hello,
 
I am trying to FTP into my Ubuntu Jeos 8.04 system.
 
I have SSH installed and running. Using putty I can log in just fine.
 
I attempted to use WinSCP to SFTP into the system. This returns an Access Denied message.
 
I have since installed vsftpd. I did edit the vsftpd config to allow local users to log in. This did not help. 
 
Upon further reading, if my understanding is correct, I actually did not need to install a seperate ftp server since I have ssh. Is this correct?
 
If I can use putty to ssh into the system, what I can do to get sftp to work? Additionally should I uninstall vsftpd?
 
Thank you,
Jose

---

### Post by oj0kksn5 on 2009-08-11
what user are you using to access the files via ssh?

you accessing it local? internet?

all i can think is to make sure that the user has rights to /

and since putty is working im assuming the port is open

---

### Post by x_jose_x on 2009-08-11
For ssh over putty I use a standard user (non-root). This works fine.
 
I am attempting to use the same user for sftp in WinSCP. I get an access denied message.
 
I am using this locally.
 
It is unlikely this user has rights to /

---

### Post by x_jose_x on 2009-08-11
This appears to be an issue with WinSCP. I just tried to log in with psftp and it works fine.
 
Edit - The issue with WinSCP was that Allow SCP Fallback option was checked. Unchecking this option worked.

---

