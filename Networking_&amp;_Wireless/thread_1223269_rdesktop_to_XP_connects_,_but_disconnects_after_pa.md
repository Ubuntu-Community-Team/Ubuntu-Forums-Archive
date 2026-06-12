---
title: "rdesktop to XP connects , but disconnects after password entry"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by newbee75 on 2009-07-26
Hi all, 

I recently installed ubuntu jaunty and having trouble with my rdesktop connection to  a XP laptop on my home network . Here is my set up : 

1) ubuntu desktop (ip 192.168.0.100) is directly connected to my router via ethernet cable. 
2) XP machine (ip 192.168.0.101) is connected to my router wirelesslessly 

3) I have enabled the rdesktop on my XP machine. 

4) I use the following command to connect to XP machine : 
    rdesktop -u kota1 -g 1280x1024 -x l -a 16 -P -D  -0 -r sound:remote 192.168.0.101

 This allows the XP desktop login/passwd screen to show up on my ubuntu box. By this, I concluded  it is able to at least "see"  the XP machine. After I enter the XP  password, it waits for  about  a min, then just disconnects without any error messages or actually showing me  the contents of the XP desktop. I made sure I am entering the right XP password.

Does anyone know what I am doing wrong ? Any help is highly appreciated!

---

### Post by newbee75 on 2009-07-26
After reading numerous websites, I found that updating my ATI driver on the XP box fixed the issue.

---

