---
title: "File Transfer From Hardy to Jaunty via Crossover"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by Macadeus on 2009-08-02
Mmk, I know that somewhere out there this question has been asked but I can't seem to get any answers that have worked.
I have a laptop running Jaunty and a desktop running Hardy. I have files on the desktop that I want to put on the laptop and there are a bunch of them, like 50 gigs. 
Previously and I mean like hours ago, I had Vista on the laptop and I linked up the two computers with a Crossover cable and dragged the files over to the Public folder in Vista and Hardy saw them just fine. 
After I installed Jaunty on the Laptop, I connected the Crossover cable but the network doesn't see Hardy at all. And I haven't messed with its settings since I did the transfer from Vista to Ubuntu.
All I want is for both computer to see each other and then I can drag and drop the files I need.
BTW, I have samba installed

---

### Post by Iowan on 2009-08-02
Assuming the machines are in the same subnet, and Workgroup, and can **ping** each other, you *might* need Winbind, but [this]("http://ubuntuforums.org/showthread.php?p=7711459#post7711459") thread would suggest otherwise. Since both machines are Ubuntu boxes, [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-to might/not help.

---

### Post by general_fault on 2009-08-31
I find the easy crossover solution to linux is using vsftpd and filezilla, 

[http://ubuntuforums.org/showthread.php?p=7878869#post7878869](http://ubuntuforums.org/showthread.php?p=7878869#post7878869)

---

### Post by JW_00000 on 2009-09-04
I'm currently in a similar situation, you might wanna take a look here: [http://ubuntuforums.org/showthread.php?t=1229814](http://ubuntuforums.org/showthread.php?t=1229814)
Lots of helpful suggestions and discussion is going on there.

---

