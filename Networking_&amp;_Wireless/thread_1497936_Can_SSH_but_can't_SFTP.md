---
title: "Can SSH but can't SFTP"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by Mad-One on 2010-05-31
Weird problem; I have set up SSH on my 10.04 server. I can putty to it over my LAN from my Win 7 box but when I try to SFTP I get "connection timed out". 

Any ideas?

---

### Post by sedawk on 2010-05-31
what happens if you login to your server (via ssh)
and then try to sftp to the server itself, e.g. with
```

sftp username@localhost
#or
sftp username@SERVER_IP_ADDRESS

```
If that works you can try to install something
like wireshark to analyse the network traffic.
The tool wireshark is available for windows and linux.

---

### Post by Mad-One on 2010-05-31
Sorry, duff info. I can't log in using ssh now. I think that i must have done something to the server between logging in ssh and trying sftp. I was left with a working ssh connection and no sftp. After a reboot both were broken. At least this is now a sensible problem.:)

Thanks for the tip about wireshark i'll give it a go.

---

