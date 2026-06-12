---
title: "Minimal NFSv4 Howto"
date: 2012-05-25
forum: Networking &amp; Wireless
---

### Post by OnnoE on 2012-05-25
Hi All,

I've written an "[NFSv4 Minimal Howto"]("https://help.ubuntu.com/community/NFSv4MinimalHowto"). I opened this thread so people can confirm that it works, make suggestions, report problems and ask for  clarifications. In other words: give feedback! This way I try to make this howto this the best resource for proper (minimal) NFSv4  setups.

From the howto:
> 
This is a NFSv4 (aka NFS4) minimal howto. Minimal in the regard that  there are minimal running resources to make a functional NFSv4 server  and client. NFSv4 can work without kerberos (read: without gssd),  without portmap (read: without rpcbind), without idmapd and without  statd. 


Regards,
Onno

---

### Post by nuclearj on 2012-08-20
I have a question, do you think there would be a difference in the instructions for installing on a real (non-virtual) host and client?

---

### Post by OnnoE on 2012-08-21
> **nuclearj said:**
> I have a question, do you think there would be a difference in the instructions for installing on a real (non-virtual) host and client?

None. I used virtual hosts for easy testing (think snapshots). This type of software is not impacted by the fact that it runs on bare metal or virtualized. I used this guide on a few "real" (as you call it) client-server combinations as well.

Regards,
Onno

---

### Post by nuclearj on 2012-08-21
Cool!  I will give it a go and report back.

---

