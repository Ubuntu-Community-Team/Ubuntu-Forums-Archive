---
title: "Played with SQL &amp; Apache2, now Samba shares don't work and no internet"
date: 2012-01-03
forum: Networking &amp; Wireless
---

### Post by GermanMafia on 2012-01-03
Hello.

This weekend I was playing with some Apache and SQL, and my Samaba shares stopped working.

I have a Windows 7 machine and an Ubuntu 11.04 machine running samba.

To my knowledge, everything worked before messing with Apache and SQL.

I can ping both machines (from each other). The Ubuntu Server comes up in the Windows network directory, but when I try to open it, it tries to communicate and times out, yielding 'network path does not exist'. 

Samba is on (sudo service smbd start --- smbd running process xxx).

The Ubuntu machine cannot see the windows network. 

Also, I have uShare running on the same machine, but Windows does not see it, it seems like Ubuntu is getting lost when trying to connect.

I disabled UFW to test, but that didn't help. 

When I was testing MySQL and Apache, I modified the my.cnf file for MySQL to change the binding address (I was trying to get access over the network). This ended up doing some funny things, but I changed it back to bind = localhost.

I have restarted the machine a few times, Apache and MySQL are both stopped. 

I don't have passwords on the samba shares (shouldn't be a user problem). 

The Ubuntu machine can see the workgroup that the Windows computers are on, but it says 'failed to retrieve share list from server'.

This is no longer a problem, but I'll leave it here in case anyone stumbles upon it. It seems that my editing of the samba config file killed the internet on the machine (lmhosts was the culprit, removing it allowed me to access the internet again). Now I'm back to the "Unable to mount location" error, but I'm guessing I'll be able to find the answer on Google.

> 
Okay bigger problem now (testing as I go): I cannot access the internet on the machine, I can't ping google (it just waits), but I can ping machines on the local network. 

I can't attach the config files as I can't access the machine (no flash drive either), but I can get them if necessary (bring out the CDs!). 

Also - I modified the nsswitch file so it has:
hosts:      files mdsn4_minimal [NOTFOUND=return] wins dns mdns4
and the samba config file to have 
name resolve order = lmhosts wins bcast host

Any ideas on what to check?

THANKS!!!!

Also Also:
Other things that may have killed my internet - I downloaded all the suggested updates to date, has there been any critical bugs in any updates lately that kill the internet? 
The server is wired to a switch, which goes to the router.

AAA:
I changed the ports.conf file in Apache to add some virtual host stuff, which I have since removed (and restarted), that still doesn't work. In the conf file I now have 'Listen *:80', , I also tried Listen 80, but that didn't work either.

Okay - The internet is back! I removed lmhosts from the samba file line, and that allowed me to get back on the internet. Although the Samba shares still don't work.


---

