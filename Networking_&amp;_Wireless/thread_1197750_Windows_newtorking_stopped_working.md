---
title: "Windows newtorking stopped working"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by LazarusHC on 2009-06-26
Hi all,

Okay, so starting with a default install of Ubuntu 9.04, I was able to access share on a Vista workgroup, no changes necessary.  One day I decided that I was to share my printer over said network, so, installed sambe, changed my workgroup name to match my workgroup, and... now I can't even access anyone else's shares, let alone share my own.  I tried uninstalling samba, reinstalling samba, reinstall smbclient... purge removing and reinstalling samba and smb client... nothing works.  All I want to do at this point, is access the share on the network again.  Any thoughts?

---

### Post by swerdna on 2009-06-26
> **LazarusHC said:**
> Hi all,

Okay, so starting with a default install of Ubuntu 9.04, I was able to access share on a Vista workgroup, no changes necessary.  One day I decided that I was to share my printer over said network, so, installed sambe, changed my workgroup name to match my workgroup, and... now I can't even access anyone else's shares, let alone share my own.  I tried uninstalling samba, reinstalling samba, reinstall smbclient... purge removing and reinstalling samba and smb client... nothing works.  All I want to do at this point, is access the share on the network again.  Any thoughts?
Name resolution across the LAN is not working.
Check samba is working withthis terminal command: sudo /etc/init.d/samba status. You should get report of smb and nmb running.
Check you've got these packages still installed: samba, libsmbclient and samba-common.

And please post the contents of smb.conf.

---

### Post by superprash2003 on 2009-06-27
try accessing by ip , what error do you face?

---

### Post by LazarusHC on 2009-06-29
> **swerdna said:**
> Name resolution across the LAN is not working.
Check samba is working withthis terminal command: sudo /etc/init.d/samba status. You should get report of smb and nmb running.
Check you've got these packages still installed: samba, libsmbclient and samba-common.

And please post the contents of smb.conf.

Smb and nmb are running and all the packages you mentioned are installed.  My smb.conf is now the default installed with Ubuntu (Let me know if you still want to see it).  Once I couldn't get it working the way I wanted, I tried to restore everything back to when it *was* working. And the only thing I changed at the time was the workgroup name. 

I'm afraid I don't know much about samba networking, so I've just been using nautilus to access windows shares.  I'm able to see the workgroup, but when I try to acces it I get "Failed to retrieve share list from server"

---

### Post by .Ix on 2009-06-29
This is exactly my problem, too. I get the same error message. Same thing happens when I use Linux Mint btw, but I have a separate /home partition that I don't touch when reinstalling. (I'm using Ubuntu 9.04 on one computer and Mint 7 on another. Same problem happens when both are running Ubuntu 9.04.)

Funny thing is, I was able to access shares and copy files on this hotel network I went to last month, and they were all probably running Windows.

---

### Post by dmizer on 2009-06-29
Please see the 6th link in my sig.

---

### Post by LazarusHC on 2009-06-29
> **dmizer said:**
> Please see the 6th link in my sig.

You are my savior!  Before starting this thread, I spent an entire day searching for a solution and didn't find anything that helped.

---

