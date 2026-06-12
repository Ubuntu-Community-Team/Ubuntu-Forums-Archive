---
title: "Help with connecting winxp to an ubuntu samba domain"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by headvampyre@hotmail.co.uk on 2009-11-29
Can Anyone help me with this please ?

I am trying to setup a samba domain and i have configured samba and can connect through my iphone and linux laptop but on xp when i try to connect to domain it asks for the username and passwords and i do not know whether to use the xp passwords or samba and it currently say connecting to the domain fails : bad username or password or user not found 

Thanks

---

### Post by pdc124 on 2009-11-29
post your samba config file 
sudo grep ^[A-Za-z\ ] /etc/samba/smb.conf

will remove all the comments 
the bit you are interested in is 

security =

---

