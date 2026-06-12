---
title: "problem on INADYN"
date: 2010-05-26
forum: Networking &amp; Wireless
---

### Post by lcx685 on 2010-05-26
Hello, 
I'm new to ubuntu. And I would like to implement INADYN to update my changing IP adress to FREEDNS, however, it does not works and google it a lot...sill have no idea. Maybe something wrong with configuration. 1.Also about the crontab, 
```
**i@ubuntu:~$ sudo crontab -e
no crontab for root - using an empty one
]29
```
so could you tell me how can I edit the file to add "@reboot /usr/sbin/inadyn"?
 
2. Even when I want to update the IP address manually, there's some problem
 
```
***:~$ inadyn --update_period 60000 -u "username" -p "password" -a chenxi.lei.chickenkiller.com --dyndns_system default@freedns.afraid.org
INADYN: Started 'INADYN version 1.96.2' - dynamic DNS updater.
I:INADYN: IP address for alias 'chenxi.lei.chickenkiller.com' needs update to '130.89.228.207'
W:INADYN: Error validating DYNDNS svr answer. Check usr,pass,hostname,abuse...!
W:INADYN: DYNDNS Server response:
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 26 May 2010 09:54:14 GMT
Content-Type: text/plain
Connection: close
Vary: Accept-Encoding
Cache-Control: no-store, no-cache, must-revalidate
Expires: Mon, 26 Jul 1997 05:00:00 GMT
Last-Modified: Wed, 26 May 2010 09:54:14 GMT
Cache-Control: post-check=0, pre-check=0
Pragma: no-cache
 
ERROR: Invalid update URL
 
W:'RC_DYNDNS_RSP_NOTOK' (0x48) updating the IPs. (it 0)
E: The response of DYNDNS svr was an error! Aborting.
 
 
 
            INADYN Help
....
W:INADYN: Main: Error 'RC_DYNDNS_RSP_NOTOK' (0x48)
```
what's the matter?
ps: here username and password are those I used to log in the freedns website

---

### Post by Piney84 on 2010-10-31
I'm also a newbie and would like to set up inadyn with freedns.
does anyone know of an easy step by step guide?

---

