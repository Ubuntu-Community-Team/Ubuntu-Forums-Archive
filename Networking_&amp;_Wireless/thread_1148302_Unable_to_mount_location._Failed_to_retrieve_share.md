---
title: "Unable to mount location. Failed to retrieve share list from server."
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by robs01 on 2009-05-04
I have a Xubuntu Samba Server connected by cable to a wireless router. A number of notebooks running windows as well as a Mac are able to access the server shares. (Music, Movies, Photos...) The problem I have is that I cannot access the workgroup to access the Server using my notebook running Ubuntu. If I boot this same notebook with Windows I a able to access the shares.
With ubuntu when I go to Places-Network, a window opens where I see 'Windows Network'. If I double click this I see my workgroup. If I double click the workgroup I get the following error: Unable to mount location. Failed to retrieve share list from server.
If someone could please help or point me to another thread as I could not find a thread with the same issue. Thanks.

---

### Post by mattgyver83 on 2009-05-08
view /etc/samba/smb.conf

Verify that your on the correct workgroup.
If you arent change it and then restart samba

sudo /etc/init.d/samba/restart

hope that does the trick.

---

### Post by Iowan on 2009-05-08
> **robs01 said:**
> 
If someone could please help or point me to another thread as I could not find a thread with the same issue. Thanks.[Here]("http://ubuntuforums.org/showthread.php?p=7236959") is one...

BTW, **sudo /etc/init.d/samba restart** works better for me... ;)

---

