---
title: "FTP server stopped working."
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by venividibitchy on 2010-01-22
I successfully set-up an FTP server, that worked great and perfectly, but after restarting the computer, it has stopped working.

None of my router's settings have changed. I restarted the vsftpd process.

What else should I try?

---

### Post by venividibitchy on 2010-01-22
Now, when I do "sudo vsftpd restart" I get:
500 OOPS: cannot read config file: restart

When I do "vsftpd /etc/vsftpd.conf" I get:
500 OOPS: could not bind listening IPv4 socket

Before, it was something else.

---

### Post by venividibitchy on 2010-01-22
Nevermind, fixed.

---

