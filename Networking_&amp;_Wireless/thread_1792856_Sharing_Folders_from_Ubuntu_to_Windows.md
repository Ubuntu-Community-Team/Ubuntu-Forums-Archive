---
title: "Sharing Folders from Ubuntu to Windows"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by omega0 on 2011-06-28
I have a computer running Ubuntu 10.10.  I am using it to share many hard drives connected to it. I am using Samba. I have successfully shared many folders to one Windows user.  I am attempting to share other folders within the shared folders to another user as read only but have not had any success.  When I attempt to connect to one of the shares from another computer running Ubuntu 10.10, logged into an Administrator account with the same username and password which I setup on the Samba share I get the error: "Unable to mount location" "Failed to mount Windows share"

---

### Post by Zymonick on 2011-06-28
Your problem description is very generic. "Unable to mount location" can refer to almost anything. Could you please post the relevant entries from /etc/samba/smb.conf and the fstab entry / mount command you are using?

---

### Post by omega0 on 2011-06-28
I have attached the mtab and smb.conf.  Let me know if there are any questions I can answer, I am not sure how to explain the problem better.   Thank you

---

### Post by omega0 on 2011-06-30
I have a share "MP3" on ubuntu which I can connect to with my "omega0" account from a Windows computer, it is a read only share and I am using Samba to share it with "Everyone".  When I attempt to access it from the same Windows computer using the "sandrea" account the error is 0x80070043.  
I have both accounts setup in Ubuntu as "administrative users" and setup in Samba as "Samba Users".

---

