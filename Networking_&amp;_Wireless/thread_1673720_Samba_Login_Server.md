---
title: "Samba Login Server"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by vader95 on 2011-01-22
Hello,

I was wondering if anybody had a howto or knew if it is possible to log  in to an Ubuntu machine with samba an Ubuntu server.  I have a pxe boot  server that does Ubuntu images and would like to authenticate users from  samba.


Thank you,
vader95

---

### Post by Naitsirhc Hsem on 2011-01-23
Cool idea, I would like to know how.  the only way I know of is to wright your own login manager

---

### Post by luvshines on 2011-01-23
Maybe you are looking for setting up Samba as PDC. That way you shud be able to login to Ubuntu server using Samba

---

### Post by vader95 on 2011-01-23
Thanks for the replies, I have thought of the PDC and was going to try it out, but do you know if you can log in ubuntu machines that way?  I was also thinking maybe NIS, do you think this would work?


Thank you,
Vader95

---

### Post by luvshines on 2011-01-23
> **vader95 said:**
> Thanks for the replies, I have thought of the PDC and was going to try it out, but do you know if you can log in ubuntu machines that way?  I was also thinking maybe NIS, do you think this would work?


Thank you,
Vader95

Well you can't store Samba information in NIS ie the NTLM hashes, SID etc
I have tried RHEL with Samba PDC, Ubuntu shud work too I guess :)

---

### Post by vader95 on 2011-01-23
I have a spare computer, I will try this on it(don't want to mess with the real server).

I appreciate the help,
vader95

---

