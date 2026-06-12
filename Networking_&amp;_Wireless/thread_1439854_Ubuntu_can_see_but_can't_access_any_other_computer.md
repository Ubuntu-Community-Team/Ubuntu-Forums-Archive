---
title: "Ubuntu can see but can't access any other computers on network"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by spartan_87 on 2010-03-26
I am using Ubuntu 9.10 and when I go to Network I can see all the other computers on my network listed, but when I click on any of them it says, "Opening "Computer-name"" and then after a few minutes it says, "Ubable to mount location: Failed to retrieve share list from server." 

I have a share set up on the Ubuntu machine and my windows computer can access it fine. So its just my Ubuntu machine having trouble accessing other computers. Do I have to edit something in my smb.conf file or something for my Ubuntu machine to access other computers? Right now I have a default smb.conf file, haven't changed anything in it.

---

### Post by oldsoundguy on 2010-03-26
Have had the same problem and it happens on almost every   kernel update in Ubuntu

Solved it by going to the windows machines and deleting permissions and then re-granting permissions.  Then re-boot everything.  Has worked on the last 3 updates for me.

---

### Post by spartan_87 on 2010-03-26
Ok, I tried that and still nothing. Its not just my windows computers though that my Ubuntu desktop cant access, it also cant access my Ubuntu laptop, which is running 9.04. And my laptop is also doing the same thing as my desktop, it can see all the computers on the network, but can't access them.

---

### Post by spartan_87 on 2010-03-26
I finally got it fixed. After searching for hours I found a thread with a similar problem and found this link in there [http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149"). Followed the steps in "Problem 2" and "Problem 3" and now both my Ubuntu machines can access shares on each other and the windows machines.

---

