---
title: "Ubuntu 8.10 FTP Server?"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by zaxone on 2009-02-01
Hi all.

I need to install an ftp server on my computer but i don't know what need to do and what is the best choice.
Can somebody tell me step by step the process?
Thanks alot

---

### Post by albinootje on 2009-02-01
> **zaxone said:**
>  I need to install an ftp server on my computer but i don't know what need to do and what is the best choice.
Can somebody tell me step by step the process?
Thanks alot

Pureftpd is a good choice (just like vsftpd) :
[https://help.ubuntu.com/community/PureFTP](https://help.ubuntu.com/community/PureFTP)

Disclaimer/reminder : You do know that by default ftp over the internet is using plain-text transfer of username/password, right ?
That's a theoretical security problem, make sure you do some reading on how to deal with this (use SSL, or ftp-users etc.).

---

### Post by zaxone on 2009-02-02
Thank you for your reply albinootje.
I followed the instructions in the link. It is not so difficult. :p

---

