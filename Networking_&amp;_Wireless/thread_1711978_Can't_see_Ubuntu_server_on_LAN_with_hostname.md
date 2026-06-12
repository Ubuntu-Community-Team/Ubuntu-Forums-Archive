---
title: "Can't see Ubuntu server on LAN with hostname"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by Ghost_Mazal on 2011-03-22
Lo Guys , I am struggling with what must probably be a very trivial problem. I have searched but can't find the answer.

I have set up an Ubuntu 10.10 server with SAMBA shares and Apache web server. Everything was working fine. Then there was a power failure and after I restarted the server the XP pc's can see the server using the hostname. They can only see it using the ip adress. I haven't change anything on server or client side. Just the restart of the server.

Can anybody help please.

Thank you

---

### Post by crispy_420 on 2011-03-22
Sounds like either a local DNS issue or WINS issue. Anyone with more experience like to chime in?

---

### Post by Ghost_Mazal on 2011-03-22
Found the problem and moved discussion over to server section. It's the NMBD not functioning correctly.

---

### Post by KillrBuckeye on 2011-03-27
Hi there Ghost_Mazal.  I'm having the same problem seeing Samba shares on my Ubuntu 10.10 machine from other devices on my network. I can connect to the shares just fine using IP address, but not with hostname.  I could not find the discussion you mentioned on the server forum.  Could you please point me in the right direction?  I think my problem is also related to NMBD, because when I try to restart the service, I get a "job failed" message.

---

