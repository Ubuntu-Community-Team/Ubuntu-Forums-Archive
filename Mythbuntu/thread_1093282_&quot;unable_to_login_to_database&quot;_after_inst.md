---
title: "&quot;unable to login to database&quot; after install from alternate disk"
date: 2009-03-11
forum: Mythbuntu
---

### Post by oneheaton on 2009-03-11
I've been having the same problems. Thanks for the advice so far...
After installing both Mythbuntu backend and frontend on the same box, I'm still getting a "no upnp server found" and "unable to login to database" error.

This happens after the install (from the alternate cd) has gone fine, then I try to either configure the backend or start the frontend.

any suggestions. 

thanks.

---

### Post by tgm4883 on 2009-03-11
Split to a new post, as this is a different problem.

---

### Post by laga on 2009-03-12
It's a known issue the database is not correctly initalized when using the alternate disk. Try running ```
sudo dpkg-reconfigure mythtv-database
```.

*edit:* It's possible you will have to dpkg-reconfigure mythtv-**common** afterwards as well do enter your database credentials.

---

