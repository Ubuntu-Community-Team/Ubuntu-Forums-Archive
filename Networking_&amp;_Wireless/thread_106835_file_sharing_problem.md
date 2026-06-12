---
title: "file sharing problem"
date: 2005-12-21
forum: Networking &amp; Wireless
---

### Post by emlee5 on 2005-12-21
Hi there

I have 2 computers, both running linux. I have successfully mounted a second hard drive on each  computer by modifying the /etc/fstab file. Each computer has been given a static IP address and they are connected via a switch to a Router which is the gateway to the internet.

I have full internet access and can ping each machine in network tools.

My problem is I just can't get the computers to see eachother. They are not under Network servers or seen via SMB4k. I have tried SMB and NFS with no luck  - I've tried the GUI interface and from the terminal, but the SMB returns and error: connection refused, or:

timeout connecting to 192.168.123.133:445
timeout connecting to 192.168.123.133:139
Error connecting to 192.168.123.133 (Operation already in progress)
10854: Connection to 192.168.123.133 failed
SMB connection failed


Can anyone please help?

---

### Post by cwaldbieser on 2005-12-21
[QUOTE=emlee5]Hi there

I have 2 computers, both running linux. I have successfully mounted a second hard drive on each  computer by modifying the /etc/fstab file. Each computer has been given a static IP address and they are connected via a switch to a Router which is the gateway to the internet.

I have full internet access and can ping each machine in network tools.

My problem is I just can't get the computers to see eachother. They are not under Network servers or seen via SMB4k. I have tried SMB and NFS with no luck  - I've tried the GUI interface and from the terminal, but the SMB returns and error: connection refused, or:

timeout connecting to 192.168.123.133:445
timeout connecting to 192.168.123.133:139
Error connecting to 192.168.123.133 (Operation already in progress)
10854: Connection to 192.168.123.133 failed
SMB connection failed


Can anyone please help?[/QUOTE]

Do you have a samba server running on each PC?

---

### Post by emlee5 on 2005-12-22
Yes I have samba server running on each pc.
I used the unofficial ubuntu guide page to install samba and smbfs and set up a password and /etc/samba/smbusers file.

I can't see the other pc under places --> Network servers.

any ideas?

---

