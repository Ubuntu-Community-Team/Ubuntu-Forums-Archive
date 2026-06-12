---
title: "[SOLVED] No remote connection from frontend to backend"
date: 2007-12-18
forum: Mythbuntu
---

### Post by Michael Deindl on 2007-12-18
Hi all!

I have a working frontend/backend machine, which actually should allow connections from outside: Both mysql and mythtv are binding to the actual IP-address, not to 127.0.0.1, which I can confirm with nmap:
----------------
nmap mythmaster1

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-12-18 20:48 CET
Interesting ports on server.lan (10.26.9.42):
Not shown: 1693 closed ports
PORT     STATE SERVICE
631/tcp  open  ipp
3306/tcp open  mysql
6543/tcp open  mythtv
6544/tcp open  mythtv

Nmap finished: 1 IP address (1 host up) scanned in 0.216 seconds
----------------

Recently I installed a frontend-only machine with mythbuntu.

I can telnet to the mythtv port on the master-backend and when I hit the button "test connection" the database connection is verified as working.

Also, when planning recordings from the frontend, I can see the EPG, so database connection obviously works fine.

However, connection to mythtv on the backend itself doesn't work.  The log says the following:
-----------------------------
2007-12-18 19:48:58.233 New DB connection, total: 1
2007-12-18 19:48:58.240 Connected to database 'mythconverg' at host: 
mythmaster1
2007-12-18 19:48:58.241 Total desktop dim: 1400x1050, with 1 screen[s].
2007-12-18 19:48:58.245 Using screen 0, 1400x1050 at 0,0
2007-12-18 19:48:59.518 Current Schema Version: 1160
2007-12-18 19:48:59.739 mythfrontend version: 0.20.20070821-1 
[www.mythtv.org](www.mythtv.org)
2007-12-18 19:48:59.739 Enabled verbose msgs:  important general
2007-12-18 19:49:19.078 Total desktop dim: 1400x1050, with 1 screen[s].

[..........]

2007-12-18 19:53:30.643 Connecting to backend server: mythmaster1:6543 
(try 1 of 5)
2007-12-18 19:53:30.643 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2007-12-18 19:53:32.746 TV: Attempting to change from None to None
-----------------------------

mythmaster1 resolves fine to my master backend.  Telnet to the port in question works fine.  Just the frontend cannot connect.

Is there any setting on the masterbackend to allow remote access besides having it listening on the external IP-Address?

It would be great, if anyone could help me!  Thanks!

Bye,
Michael

---

### Post by superm1 on 2007-12-18
> **Michael Deindl said:**
> Hi all!

I have a working frontend/backend machine, which actually should allow connections from outside: Both mysql and mythtv are binding to the actual IP-address, not to 127.0.0.1, which I can confirm with nmap:
----------------
nmap mythmaster1

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-12-18 20:48 CET
Interesting ports on server.lan (10.26.9.42):
Not shown: 1693 closed ports
PORT     STATE SERVICE
631/tcp  open  ipp
3306/tcp open  mysql
6543/tcp open  mythtv
6544/tcp open  mythtv

Nmap finished: 1 IP address (1 host up) scanned in 0.216 seconds
----------------

Recently I installed a frontend-only machine with mythbuntu.

I can telnet to the mythtv port on the master-backend and when I hit the button "test connection" the database connection is verified as working.

Also, when planning recordings from the frontend, I can see the EPG, so database connection obviously works fine.

However, connection to mythtv on the backend itself doesn't work.  The log says the following:
-----------------------------
2007-12-18 19:48:58.233 New DB connection, total: 1
2007-12-18 19:48:58.240 Connected to database 'mythconverg' at host: 
mythmaster1
2007-12-18 19:48:58.241 Total desktop dim: 1400x1050, with 1 screen[s].
2007-12-18 19:48:58.245 Using screen 0, 1400x1050 at 0,0
2007-12-18 19:48:59.518 Current Schema Version: 1160
2007-12-18 19:48:59.739 mythfrontend version: 0.20.20070821-1 
[www.mythtv.org]("http://www.mythtv.org")
2007-12-18 19:48:59.739 Enabled verbose msgs:  important general
2007-12-18 19:49:19.078 Total desktop dim: 1400x1050, with 1 screen[s].

[..........]

2007-12-18 19:53:30.643 Connecting to backend server: mythmaster1:6543 
(try 1 of 5)
2007-12-18 19:53:30.643 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2007-12-18 19:53:32.746 TV: Attempting to change from None to None
-----------------------------

mythmaster1 resolves fine to my master backend.  Telnet to the port in question works fine.  Just the frontend cannot connect.

Is there any setting on the masterbackend to allow remote access besides having it listening on the external IP-Address?

It would be great, if anyone could help me!  Thanks!

Bye,
Michael
In mythtv-setup, there are *two* sections for an ip address.  Make sure you have modified **both.  **

---

### Post by Michael Deindl on 2007-12-19
I checked mythtv-setup and changed both IP-Addresses from hostnames to actual IP-numbers.

Now the frontend connects fine.  I have no idea why that is, because the hostname resolves OK through my local DNS-server.

Maybe somewhere within mythtv it is hardcoded to use IP-numbers instead of hostnames?

Bye,
Michael

---

### Post by uopjohnson on 2007-12-19
yea myth has never resolved names properly though it does use the host name to set the individual frontend preferences.  Annoying, but  reality.

---

