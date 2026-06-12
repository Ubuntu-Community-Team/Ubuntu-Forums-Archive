---
title: "SADMS - Can't see machine within Windows"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by DLLong on 2009-12-08
I just added a second Ubuntu server (Server4) to my Windows network.  I used SADMS and everything seemed to set up fine.  I can go to the W2K3 domain controller look in Active Directory and the machine shows up just fine right along side the other Ubuntu server (Server3) on the network.

Here's the problem.  If I try to access the new machine (Server4) using Windows Explorer, it does not show up.  Server3 shows up fine and I can browse through the folders,etc.

I've obviously missed a step somewhere but am at a loss.  When I look at the status screen for SADMS, everything is "green" and good to go.

Can someone help me out by giving me some suggestions on what is missing as to why the Windows domain can see one Ubuntu server but not the other?

---

### Post by DLLong on 2009-12-08
BTW, one other thing I've noticed is that if I am using "sudo", on the new server it asks for the password.  However, on the old server that I can see it asks for both the password and the pam_mount password.  Not sure if that means anything or not.

---

