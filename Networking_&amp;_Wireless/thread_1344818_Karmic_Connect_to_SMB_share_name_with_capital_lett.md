---
title: "Karmic: Connect to SMB share name with capital letter through GUI"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by krimskrams on 2009-12-03
Hi,

I have a strange problem ... I try to connect to a windows share which has a capital letter in it through the "Connect to server" dialog of Ubuntu Karmic. 

IP: 192.168.123.2
Share: Volume_1

In the following window for entering the password I can see that the share name is converted to lower letters ... therefore no connection can be established.

Using a command line works like a charm:
sudo mount -t smbfs -o user=<user> //192.168.123.2/Volume_1 /mnt
works perfectly.

Any ideas?
Krimskrams

---

