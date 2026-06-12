---
title: "samba connects as smbguest"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by aaronp on 2010-06-20
Hi all,

I've set up a samba share on my Karmic server and created a user on the machine, which was also added with smbpasswd -a

I am successfully connecting from my other Ubuntu PC (Lucid) but when it connects, the permissions on the mountpoint are 
smbguest / sambamachines

Then, at the next level down the permissions are all:
smbguest / nobody

I am connecting with the correct username and password so not sure why it's defaulting to the guest account. 

Can anyone assist?

thanks
Aaron

---

### Post by aaronp on 2010-06-20
bump

---

