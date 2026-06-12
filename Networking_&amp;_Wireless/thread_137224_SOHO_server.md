---
title: "SOHO server"
date: 2006-02-27
forum: Networking &amp; Wireless
---

### Post by slimvad on 2006-02-27
I'd like to make a multipurpose SOHO server out of my Linux box. The problem is even thoug I've got quite some experience with Win32, I'm a complete newbie with Linux.

The network architecture is as follows:

WinXP box (x3)
|
Home switching hub
|
eth1 @ Linux box
|
[A spacer for whatever software I'll have to install to accomplish the task]
|
eth0 @ Linux box
|
ISP's switching hub
|
ISP's VPN server
|
Internet

The functions the server should perform are listed below (ordered by priority):

1. Firewall / NAT
2. Caching proxy
3. Web server
4. FTP server
5. Domain server
6. Automated fax (saving incoming messages in pdf (or whatever) format)

What software should I use to make it work?
From what I've already learnt it's got to be something like this:

1. Iptables
2. Squid
3. Apache/php/postgre or mysql
4. NO IDEA
5. Samba
6. NO IDEA

Please give me some clues on 4. and 6.
Any ideas on how to improve the server's functionality are welcome.

---

### Post by claes on 2006-02-27
[QUOTE=slimvad]
4. NO IDEA
5. Samba
6. NO IDEA
[/QUOTE]

4. Proftpd, vsftpd or wu-ftpd   ( I would use proftpd but you might like the other ones)
6. hylafax-server    

Claes

---

### Post by mips on 2006-02-28
[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

4. Would something from the repositories be sufficient, just look for FTP ?

---

