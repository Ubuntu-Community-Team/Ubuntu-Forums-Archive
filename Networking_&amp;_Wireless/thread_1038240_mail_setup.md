---
title: "mail setup"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by gnikol1974 on 2009-01-12
hi
I would like to perform the following configuration and I would like to ask your advice.
This is what I would like to do:
I have two pop3 mail accounts in the internet. 
I want to setup on mail server which will download and sent emails.
I will use thunderbird to collect the emails from 2 different PCs.

I have download fetchmail and is working but I am having problem to integrate it with sendmail??? or such application.

Can you help me on this small  project?

Thanks a lot
George

---

### Post by albinootje on 2009-01-12
> **gnikol1974 said:**
>  I have download fetchmail and is working but I am having problem to integrate it with sendmail??? or such application.


Getmail is an interesting alternative for fetchmail :

[http://www.howtoforge.com/debian_etch_getmail](http://www.howtoforge.com/debian_etch_getmail)
[http://www.livadaru.net/cristian/wiki/index.php/Getmail](http://www.livadaru.net/cristian/wiki/index.php/Getmail)

I would like to recommend using dovecot as local imap/pop3 server on your own server, and postfix as your local smtp-server to send out emails.
It's fairly easy to set up.

sudo apt-get install postfix dovecot-imapd dovecot-pop3d

See here for more information :
[http://www.debian-administration.org/articles/275](http://www.debian-administration.org/articles/275)

---

