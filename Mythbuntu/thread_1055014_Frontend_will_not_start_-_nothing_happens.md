---
title: "Frontend will not start - nothing happens"
date: 2009-01-30
forum: Mythbuntu
---

### Post by Fkewl on 2009-01-30
Hi,

I have a functionnal backend (ibm thinkcentre, mythbuntu 8.1) and i took my second thinkcentre to create a frontend.  

I successfully configured and had a working frontend until an update i did last night.  Now the frontend won't even appear.

(double-clic icon, nothing appears) 

I've tried reinstalling mythbuntu-frontend, but still no screen.  I can open mythbuntu control center and test the connection (successful) to the backend (192.168.1.107). 

How do i go about analyzing what's happening ?

---

### Post by alderion on 2009-01-30
try starting mythfrontend from the command line and see if it tells you anything.  i think you can also check /var/log/mythtv/mythfrontend.log for any errors.  you can also pass mythfrontend a -v arg with kerywords such as 'all' or 'video'.  check mythfrontend -h for the particulars.

-peter

---

