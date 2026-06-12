---
title: "MythTV 0.27 Frontend on Windows won't connect to Mythbuntu 14.04 backend"
date: 2015-10-02
forum: Mythbuntu
---

### Post by tristan-dawson on 2015-10-02
Hi all, I recently downloaded a MythTV 0.27 build for Win8.1 from ([http://sourceforge.net/projects/mythtvwindows/](http://sourceforge.net/projects/mythtvwindows/)), but can't seem to get it to connect to my Mythbuntu 14.04 frontend/backend PC. :(

The windows MythTV frontend just always says "Could not connect to master backend" with a huge red 'X', even though I'm sure I've setup all the options correctly under Setup --> General in the frontend..... But perhaps I'm missing some steps.. I can certainly ping my mythtv PC from my Win81 PC and vice versa, i can even VNC to the MythTV PC from my Win81 PC.

Can someone please help me out? I'm trying to cut ads out of recordings from a frontend on my Win81 PC...

Thanks heaps!
-Tristan

---

### Post by dmjenso on 2015-10-02
Be sure to double check the password in the frontend Setup > General.  Mythbuntu 14.04 (if I remember correctly) set a random password on the mythconverg DB at install.

---

### Post by tristan-dawson on 2015-10-05
Thanks, but I've checked that.. My Backend Machine has a frontend also and I've copied the settings from that machine onto my windows frontend, but it still says:
"Could not connect to master backend
MythContext
Could not connect to the master backend server. Is it running? is the IP address set for it in mythtv-setup correct?"

Help?

Is it possible it's being blocked somewhere by a firewall or the like?

---

### Post by aelfric55 on 2015-10-11
mysql (mariadb) on the backend has to be configured to an actual IP address on your network (not localhost nor 127.0.0.1)  and configured to accept connections via TCPIP from regular IP addresses, not just locally from  msql.

---

