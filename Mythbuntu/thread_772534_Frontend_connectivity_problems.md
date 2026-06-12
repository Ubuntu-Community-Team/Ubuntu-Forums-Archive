---
title: "Frontend connectivity problems"
date: 2008-04-28
forum: Mythbuntu
---

### Post by smbm on 2008-04-28
I seem to be getting a bizarre problem.

My frontend (on my laptop, installed over a standard Hardy install) cannot connect to my backend (which is on my server).

I can connect via VNC, mysql (so it's not a database problem) and ping (so it's not a total lack of connectivity problem) to the backend but not via Myth.

I definitely have the mythconverg database and the backend is definitely working on some level because Mythweb works and so does my dads windows based Myth frontend!

Can anyone help me diagnose/fix this? 

Thanks in advance.

---

### Post by volkswagner on 2008-04-28
What versions of Mythtv are each machine?  Post frontend.log and backend.log from respective machines.  They are located in /var/log/mythtv/

---

### Post by smbm on 2008-04-28
Cheers for your reply,

I've found the problem. It's in the frontend log.

```

2008-04-28 16:52:14.797 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-28 16:52:14.798 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
```

is the offending bit.

My backend is 192.168.0.4

The database is connecting fine. When I look at the settings page in the Myth frontend it says 192.168.0.4

Bizarre.

Which config file is this info stored in?

I checked /etc/mythtv/ but couldn't see anything useful in there.

Any ideas?

---

### Post by justanotherhack on 2008-04-28
You should normally be able to configure that directly in MythTV.

Anyway, the setting is stored in the MySQL database.

Connect to it:
```
mysql -u mythtv -p mythconverg
```
Find the line:
```
SELECT * FROM settings;
```
Alternative:
```
SELECT * FROM settings WHERE columnname_for_values='127.0.0.1';
```
And change it
```
UPDATE settings SET columnname_for_values='new_value' WHERE columnname_for_key='name_of_backendipconfig';
```

Sorry for not supplying the correct field names for the database, but I don't have a machine running here, have to check back at home. But I'm sure you'll find out.

---

### Post by smbm on 2008-04-28
I managed to sort it out.

Armed with the last post I wen to administer my backend and realised that the server IPs had not been set properly and that the frontend got the server IP out of the database (what an odd system).

Anyway, all working spiffingly now.

Cheers very much.

---

