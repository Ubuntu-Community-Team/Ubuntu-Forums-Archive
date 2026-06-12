---
title: "vsftpd and Mac"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by darthpenguin on 2010-08-14
Hey guys

I have Windows, Linux, and Mac machines. I want to be able to share files between all my machines in a consistent fashion. juggling between afp smb ssh etc is bothersome. because I am not concerned about security in my home network I thought I'd just setup an ftp server on each machine. I installed vsftpd on ubuntu. when I connect to the vsftpd server from my mac using "Connect to server..." I have no write privileges. When I connect using cyberduck I can upload fine. I'd rather use "Connect to server.." how can I get this to work.

---

### Post by gordysc on 2010-08-14
What's in your /etc/vsftpd.conf?  Since you aren't to concerned with security, do you have the anonymous settings enabled?

---

### Post by darthpenguin on 2010-08-14
I just did some more googling. it seems that Apple's Finder simply dosn't have ftp write support. It sucks. I'll just use cyberduck. :(

---

