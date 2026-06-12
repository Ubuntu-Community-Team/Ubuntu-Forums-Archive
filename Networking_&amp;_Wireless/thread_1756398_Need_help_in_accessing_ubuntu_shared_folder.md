---
title: "Need help in accessing ubuntu shared folder"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by kriss332 on 2011-05-12
hi 2 all,
i have connected an ubuntu PC on LAN and created a shared folder on desktop. Now the issue is- I can access this folder through server (2008) ( by simply typing IP of that Ubuntu PC in network places). but it doesnt work when i try 2 access the same through a LAN PC running on XP. It gives an error message - " the access to this place has been disallowed". do i have to assign some extra permissions in ubuntu? plz guide...
 Thanx in advance...

---

### Post by ksprasad on 2011-05-12
Hi,
 
How r u trying to access it?
 
Open run and type: [\\<ip]("file://\\<ip") address>\
 
It always works for me.
 
Regards,
ksprasad

---

### Post by kriss332 on 2011-05-12
Thanx prasad, 
If i hav to open shared from windows pc i do- 'my network places' then:-  \\<ip address of ubuntu pc>\
But user PCs give error- 'disallowed'. But it opens by same way from server.
Unfortunately, most of the user PCs cant open 'RUN COMMAND' coz it is disabled for security purpose. So i cant ask them to go thru RUN command also. Is there any possibility of any other problem? May b, coz servers run on admin, & other users with simple users (with no admin rights). 
though 2mrw i'll try 2 access it from admin of user PC. Lets c, will let u know.
Thanx for reply.

---

### Post by kriss332 on 2011-05-13
Today i checked with run command and <IP Address of ubuntu PC>, it opens up. But  Run command has been disabled on LAN XP users, Run will be available only on Win 07 users. So, is there any other way to access Ubuntu shared from low privileged users. Can it be any issue of permissions to be assigned in Ubuntu shares??? 
Thanx...

---

### Post by kriss332 on 2011-05-13
guys...anybody with any ideas???

---

