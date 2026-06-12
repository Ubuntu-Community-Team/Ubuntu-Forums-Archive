---
title: "Primary DNS lost after reboot"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by codescribler on 2009-04-21
Hi All,

Each time I boot up my Ubuntu installation I have to update my DNS settings before i can get on the internet. When I boot up my wired connections says I am connected (to the local network I assume). But is unable to resolve any external addresses. I right mouse click on the connection icon and select  Edit Connections. I select the Auto eth0 and select the Edit button then select IPV4 settings. I then select DHCP (address only) from the drop down and then put in my ISP's DNS address. After disconnecting and reconnecting this allows me to connect. 

1. Why when my windows XP box doesnt need any such help do i need to do this each time?
2. How do I make the setting stick (if thats what I actually need to do)?

Thanks in advance,

Codescribler

---

### Post by Iowan on 2009-04-21
A couple of things - if you use DHCP, you can edit */etc/dhcp3/dhclient.conf* and include your preferred DHS server on the "prepend" line.  [This]("http://ubuntuforums.org/showthread.php?t=971064") thread has another option.

---

