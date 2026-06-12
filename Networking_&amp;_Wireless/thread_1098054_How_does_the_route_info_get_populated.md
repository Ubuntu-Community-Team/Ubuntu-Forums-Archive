---
title: "How does the route info get populated"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by RMSe17 on 2009-03-16
I have an Ubuntu server that has two network cards, one of them is used for iscsi (eth1) and the other is used for everything else (eth0).  Whenever I restart the unit, it gets a line in the route that tells everything to use eth1, and then another line that tells everything to use eth0.  Both are labeled "default".  I can't connect to the box remotely, nor can the box perform any of it's functions unless I go to the server, log in, and manually run  "sudo route del default" after which everything works fine. 

Where does this line come from?  What has access to the route during the restart procedure?  I need to edit that, and remove the unwanted line...
I may have edited some config file that i have forgotten about, since getting the two network cards to work properly required me to edit stuff in some locations.  I did all the editing while looking at various forum posts, and I dont remember what I did. 

Thanks,
RMSe17

---

