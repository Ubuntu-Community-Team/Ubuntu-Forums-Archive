---
title: "Problems to connect with Windows 7 shares..."
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by McMichael on 2010-12-20
Hi, I have a machine with Windows 7 Ultimate with several shared folders. Then I have VMWare with Ubuntu 10.10 as guest running. Samba runs in Ubuntu and in Windows, I can see the shared folders of the Ubuntu guest (read and write) as well. This morning I saw the shared folder of the Windows host and I could still open it manually in the Ubuntu guest. After this, I wanted to mount the folders permanently with fixed entries in the /etc/fstab. This failed and now I can't see the folders of the Windows host in the Ubuntu guest... :-((( Can someone help me please!? Thank you in advance!

---

### Post by McMichael on 2010-12-20
Hello, it seems that I have the same problem ... here the result of my "smbtree"!

---

### Post by capscrew on 2010-12-20
> ****McMichael** said:**
> Hello, it seems that I have the same problem ... here the result of my "smbtree"!

Although the symptoms might be similar, I'll bet the root cause will turn out to be different.  My suggestion is for you to start a your own thread.  You can use this in the title "...with **negprot: ERRnomem** as an error"

Edit:  For clarity the above was originally posted at another thread.  It was moved here to this thread.

The **negprot: ERRnomem** could mean that the host is not online.  This usually occurs when there is no response to the initial negotiation of the connection.

---

### Post by capscrew on 2010-12-20
> **McMichael said:**
> Hi, I have a machine with Windows 7 Ultimate with several shared folders. Then I have VMWare with Ubuntu 10.10 as guest running. Samba runs in Ubuntu and in Windows, I can see the shared folders of the Ubuntu guest (read and write) as well. 
From where to where?  Are these hosts all on one physical machine?  What have you done for basic TCP/IP networking?  What are the IP addreses of the 2 hosts.  What are their **hostnames**? > 
This morning I saw the shared folder of the Windows host and I could still open it manually in the Ubuntu guest. After this, I wanted to mount the folders permanently with fixed entries in the /etc/fstab. This failed and now I can't see the folders of the Windows host in the Ubuntu guest... :-((( Can someone help me please!? Thank you in advance!
What did you do?  What failed?

---

