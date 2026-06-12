---
title: "Samba help"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by randumnumber on 2009-11-27
I recently installed Mythbuntu on one of my machines, it all works fine, except one thing. 

I successfully set samba up and shared the video folder on my network. I can browse to the video folder on my mythbuntu machine from my laptop running ubuntu. BUT, when i try to drag folders from my laptop to my mythbuntu machine it says
CAN NOT WRITE TO FILE - im not sure if its because of a permissions issue or something else.

I checked the smb.conf file and writable is set to yes for the video folder. 

I have tried to follow multiple guides to setup/trouble shoot samba, but they all say something to the effect of make sure writeable is set to yes, which it is.

This is frustrating because i want to transfer my music and videos off my laptop to clean it up, but cannot because of this issue, any suggestions?

Please email me if you have useful info, 

[email]Randumnumber@gmail.com[/email]  Thanks.

---

### Post by Iowan on 2009-11-27
You might try adding your username to a **write list=** option line.

---

