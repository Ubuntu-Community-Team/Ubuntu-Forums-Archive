---
title: "general networking (wired) less reliable since upgrading to 12.10"
date: 2013-03-24
forum: Networking &amp; Wireless
---

### Post by jonandel on 2013-03-24
Hi All,

Im newish to Ubuntu.
I had Ubuntu 12.4 running fine on my Pentium based machine, but since upgrading (I did a clean install) of Ubuntu 12.10, I now get intermittent networking 'holdups'.  The symptoms are things like 
- VLC simply not playing a network file.  It hangs, and I cannot kill the VLC session.
- Libre Office saying 'file does not exist', when I try to save a new file, and then refuses to show the File Save as dialogue box
(in both cases, I've used the connect to Remote server from the FIle menu, and connected either as webdav, or Windows (I assume is SMB) etc.

Having said this, in general other networking activities seem fine 

How do I diagnose such a problem ?
Where can I start looking for hints to what is going on ?

---

### Post by dabl on 2013-03-24
Can you tell more about the network configuration?

-- What is the remote filesystem?
-- NFS, SAMBA, IP-only?

---

### Post by NetworkNerd7 on 2013-03-24
Have you tried the connection on another computer to see if it is Ubuntu or your network?

---

