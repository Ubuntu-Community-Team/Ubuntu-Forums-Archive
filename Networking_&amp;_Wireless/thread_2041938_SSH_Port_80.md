---
title: "SSH Port 80"
date: 2012-08-13
forum: Networking &amp; Wireless
---

### Post by shibby4555 on 2012-08-13
I've been at this for a while and have not found a concise solution. Trying to set up an SSH connection over port 80 to my Ubuntu Server from my University Wifi. 

I'm weary of tampering too much with port 80, with the fear of throwing off my web server though it goes through web traffic is forwarded to internal port 8080.

I hope I am being concise here, my brains a little bit jarred at this point.

---

### Post by hawkmage on 2012-08-13
If you are not using port 80 for Apache where tampering with port 80 will not affect Apache.  If Apache or some other service is using port 80 then you are out of luck since you can only bind 1 service to an IP address/port combination.

If you want to change the port sshd is listening on then edit the line in the /etc/ssh/sshd_config that starts with "Port" to have 80 instead of 22 or you can add annother Port line with 80 in adition to 22 that way it will listen on both 22 and 80.

---

