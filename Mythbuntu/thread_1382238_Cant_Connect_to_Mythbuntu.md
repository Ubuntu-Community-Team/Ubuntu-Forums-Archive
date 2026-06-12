---
title: "Cant Connect to Mythbuntu?"
date: 2010-01-15
forum: Mythbuntu
---

### Post by PlatosGimp on 2010-01-15
I am running the latest Mythbuntu on a machine serving as both the backend and a frontend. Other than dealing with some remotely mounted media which are not yet seen, tv and recordings work fine. So I setup mythtv-frontend on another Ubuntu 9.10 laptop. I changed the backend settings so mysql is bound to all nics and I can connect ok with

mysql mythconverg -h 192.168.1.192 -u mythtv -p

So on the new front end, I set the correct IP, username (mythtv) and default database, same as in the line above and VERY carefully typed in the password multiple times, but it still cant connect to the remote backend? How can this be since it connects fine from the shell?

Any ideas?

---

### Post by williammanda on 2010-01-15
Goto mythbuntu control center and select mysql and input your info and test to see if it works.

---

### Post by radnor on 2010-01-19
> **PlatosGimp said:**
> Other than dealing with some remotely mounted media which are not yet seen, tv and recordings work fine.

Any ideas?

TV and recording work fine.  Problem with your MUSIC on the BE (not playing on a RFE)???  If so, on the RFE make a NFS connection to the BE and your music will play.  I can "SEE" my music on a RFE but NOT play it until I make the NFS connection.

---

### Post by klc5555 on 2010-01-19
> **PlatosGimp said:**
> I am running the latest Mythbuntu on a machine serving as both the backend and a frontend. Other than dealing with some remotely mounted media which are not yet seen, tv and recordings work fine. So I setup mythtv-frontend on another Ubuntu 9.10 laptop. I changed the backend settings so mysql is bound to all nics and I can connect ok with

mysql mythconverg -h 192.168.1.192 -u mythtv -p

So on the new front end, I set the correct IP, username (mythtv) and default database, same as in the line above and VERY carefully typed in the password multiple times, but it still cant connect to the remote backend? How can this be since it connects fine from the shell?

Any ideas?

Did you set the PIN to 0000 in the backend setup?

---

