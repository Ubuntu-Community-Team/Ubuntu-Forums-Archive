---
title: "Connecting two Ubuntu Computers"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by mnielsen1984 on 2009-03-03
I'm trying to connect two Ubuntu computer together to file and Internet sharing

My main Ubuntu machine is a desktop running Ubuntu 8.04 with a direct connection to the Internet via a Cable modem.  I have another cable running to a router that has connections going to another desktop that is used to experiment on, with another cable that I use to connect to my laptops (one running Windows XP).

I would like to be able to connect my Ubuntu 8.04 desktop to the laptop running Ubuntu 8.10 to share files and an Internet connection.

Thank you,
mnielsen1984

---

### Post by x22 on 2009-03-04
with a crossover cat5 cable you can connect the network
ports of the two machines: then you can use ftp to transfer
files from one to the other

alternatively, using NFS, you can mount directories on one
machine, in the heirarchy of the other, and copy files directly

sharing the internet connection is also possible, using iptables
and masquerading.  Suggest reading the various HOWTOs such as the Masquerading-Simple-HOWTO.gz in /usr/share/doc/HOWTO.

---

### Post by juan234 on 2009-03-04
You could always use ssh and nautilus (places -> connect to server -> ssh) to connect on your LAN.

---

### Post by Iowan on 2009-03-04
Sounds like the bases have been covered... almost - sharing with the Windows machine may require Samba (although Putty will let Windows SSH into Ubuntu).

---

