---
title: "rdesktop and hostname-IP resolving"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by greenerpole on 2010-08-17
Dear all, 

I had the error message "Error: getaddrinfo: Name or Service not known" trying to log in to the Windows server at my work, from my laptop (Ubuntu 10.04, fresh install) using rdesktop. The protocol is rdp and I am supposed to provide both a server name and gateway name. I tried tsclient and gnome-rdp and got the same message.

I tried to connect from a Windows computer and had no problem, so I know that the connection information (machine name, gateway hostname, username, password) are correct and that the remote machine works alright. 

Reading through other threads in the forum, a possible solution would be to provide an IP address instead of a machine name. Indeed, when i use 'dig machinename', it fails to give me any answer for the IP. The question is: where can i find such an IP address? And why could Windows find it and not Ubuntu?

Thanks for any answer to this. 
Cheers.

---

