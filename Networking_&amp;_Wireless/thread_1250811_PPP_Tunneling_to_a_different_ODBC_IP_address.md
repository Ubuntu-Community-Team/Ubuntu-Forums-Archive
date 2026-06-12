---
title: "PPP Tunneling to a different ODBC IP address"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by pwpeterson on 2009-08-27
Hi,  I'm running Ubuntu 9.04 on my VPS.  

I created a VPN PPP tunnel to a server with an IP  address of 11.12.n.n

I alse installed unixODBC and IBM's iSeriesAccess to create a ODBC connection to a AS400 server.

After establishing the PPP tunnel I tried to test the ODBC connection with 
-isql -v myVPN

Which returned:
[08S01][unixODBC][IBM][iSeries Access ODBC Driver]Communication link failure. comm rc=10065 - CWBCO1003 - Sockets error, function  returned 10065, 10.81.n.n
[ISQL]ERROR: Could not SQLConnect

You can see the VPN's IP address is 11.12.n.n while the ODBC connection is at 10.81.n.n.

I tried to ping the ODBC connection after establishing the PPP connecton but it says the Destination Host Unreachable.

I have a similar setup on my WIn XP workstation and can reach the ODBC connection without a problem after make the VPN connection.

What do I need to do to get my PPP tunnel to allow connections to the ODBC connection?

Thank for any assistance.

owo

---

