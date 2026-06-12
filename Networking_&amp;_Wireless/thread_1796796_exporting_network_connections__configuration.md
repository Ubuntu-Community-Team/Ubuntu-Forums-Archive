---
title: "exporting network connections \ configuration"
date: 2011-07-04
forum: Networking &amp; Wireless
---

### Post by brunobliss on 2011-07-04
Hey guys i'm currently using ubuntu 10.04 and wanted to update to 11.04 and that means backing up all sorts of data and configuration.

Regarding the wireless configuration list, i have a few with password and auto connect, i wanted to know if there is a way of saving that list\configuration other then manually.

thanks in advance!

---

### Post by Bucky Ball on 2011-07-04
Install 11.04 on a different partition, use the existing /home for both users, then just copy from one file to the other. The other bonus is that you have an working install if and/or when you have problems with setting up 11.04. 

Why exactly do you want to upgrade to 11.04 from a functioning LTS release? Just curious ...

---

### Post by brunobliss on 2011-07-04
So what you are saying is that, i backup my /home folder, install ubuntu and copy\overwirte the new /home folder with the old one and everything will be fine?

---

### Post by Bucky Ball on 2011-07-04
Nope. I am assuming you have a separate /home partition. In manual partitioning during install of 11.04 you just leave the existing /home (mark to use it, but *NOT* to format). The new install will then consider the existing /home partition to be *its* /home partition also.

So you wind up with /user1 and /user2 in the /home partition. Then copy settings from one to the other.

---

