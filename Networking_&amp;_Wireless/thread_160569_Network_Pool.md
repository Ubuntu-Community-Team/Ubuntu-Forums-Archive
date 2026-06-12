---
title: "Network Pool"
date: 2006-04-15
forum: Networking &amp; Wireless
---

### Post by utab on 2006-04-15
Dear all, 

At work, we have a document pool where we share documents and important files with colleagues. Every time I reboot I have to run a small script to mount this pool, here comes the script(supplied by a friend.)

 export USER=username%password
 smbmount //filesrv/homes /home/utab/documents/MECH_HOME -o  uid=utab,gid=utab
 smbmount //filesrv/pool /home/utab/documents/MECH_POOL -o uid=utab,gid=utab
 export USER=username%password
 # smbmount //10.33.175.17/mdmunck /home/utab/et/home_gandalf -o uid=maarten,gid=maarten
 export USER=

I would like to mount these permanently. 

Thx for all in advance.

---

