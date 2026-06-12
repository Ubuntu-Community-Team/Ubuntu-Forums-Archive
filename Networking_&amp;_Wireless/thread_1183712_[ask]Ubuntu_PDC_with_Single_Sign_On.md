---
title: "[ask]Ubuntu PDC with Single Sign On"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by brightstar on 2009-06-10
Anyone please guide me, what should i do ?

Using setup from [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760), i sucessfully build PDC with OpenLDAP + Samba.
I want to implement a single sign on environtment for all of my server using this PDC from above thread.
So, i want this server using single sign on, so that user don't need to repeat enter the username and password everytime : 
- Mail server
- Proxy Server
- Web Server Application

Anyone could help me, what should i do to setup ?

---

### Post by puppywhacker on 2009-06-10
I think the keyword to look for is: kerberos

---

### Post by brightstar on 2009-06-12
yes, i have heard about kerberos too, any guide that can help me to integrate Ubuntu PDC with kerberos ?
because i already do some googling and many of them are to integrate their Ubuntu to Active Directory in Windows.

My problem is, i'm not joining any Ubuntu to AD, because i want to replace my Windows PDC with this Linux PDC using OpenLDAP + Samba in above link with single sign on capability.

---

### Post by brightstar on 2009-06-29
Anyone can help me ?

---

### Post by albinootje on 2009-06-29
> **brightstar said:**
>  My problem is, i'm not joining any Ubuntu to AD, because i want to replace my Windows PDC with this Linux PDC using OpenLDAP + Samba in above link with single sign on capability.

I guess that the answer only lies in Samba version 4, which is still in development.

[http://wiki.samba.org/index.php/Samba4](http://wiki.samba.org/index.php/Samba4)

---

### Post by brightstar on 2009-06-29
So, there is impossible to implement Single Sign On which i describe in above post with current Samba version ?

---

