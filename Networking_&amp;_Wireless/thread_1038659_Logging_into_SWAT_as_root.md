---
title: "Logging into SWAT as root"
date: 2009-01-13
forum: Networking &amp; Wireless
---

### Post by akelsall on 2009-01-13
Can someone tell me how to log in as root when using SWAT? When I use my login credentials, all that swat gives me is four icons (none of which is Globals). Since by default Ubuntu doesn't create a root user, how am I supposed to log in as root to configure smb.conf via SWAT?

Thanks,

Andy

---

### Post by akelsall on 2009-01-15
From a post I made at LinuxQuestions.com, I found my answer. I added a root password (only temporary), and can now access swat and see all the icons needed to modify the smb.conf file.

To do this, enter **sudo passwd root** and create a root password. To disable root access when you're finished modifying swat, edit your **/etc/shadow** file. Look for root. Change the second "field" (immediately following root) to "!". You can leave all the other fields as they are. The second field is the password field. 

Andy

---

