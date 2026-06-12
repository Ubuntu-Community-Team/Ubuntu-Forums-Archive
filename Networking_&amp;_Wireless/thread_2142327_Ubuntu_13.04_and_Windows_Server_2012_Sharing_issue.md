---
title: "Ubuntu 13.04 and Windows Server 2012 Sharing issues"
date: 2013-05-05
forum: Networking &amp; Wireless
---

### Post by pikohn on 2013-05-05
Hello, 

I have tried to auto mount a share in ubuntu from a windows 2012 server that is acting as a File Server. The server uses Active Directory to grant access to the files being served. I installed cifs-utils on my ubuntu machine, and still can't mount the share. I am trying to do this by editing /etc/fstab.

Here is what's currently in my fastab:

//shareserver  /home/userl/Windows cifs uid=1000,user=domain/user,password=pass 0 0

When I try to mount manually I get:

mount error(6): No such device or address

Also, when putting in the wrong password manually I get the error permission denied. When I put in the right password, however, that's when I get error 6. I'm not sure what's going on here. :confused:

Thanks to anyone who can help me with this problem. :D

Mike

---

### Post by 2F4U on 2013-05-05
I guess you would have to configure Samba to join the Active Directory:

[https://help.ubuntu.com/10.04/serverguide/samba-ad-integration.html](https://help.ubuntu.com/10.04/serverguide/samba-ad-integration.html)

---

### Post by pikohn on 2013-05-05
Thanks for the reply,

It seems that there were some formatting errors with my fstab. I had to make aliases for my windows shares with no spaces and it worked. So my question is, how do you handle shares that have spaces when mounting with cifs?

Mike

---

