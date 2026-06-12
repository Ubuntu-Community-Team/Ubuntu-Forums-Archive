---
title: "port doesn't want to open"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by private_click on 2011-02-15
hi.

i have trouble opening a port on a vps running ubuntu 10.04.
the firewall i am currently using is ufw.it is already configured for SSH, Apache, MySQL, FTP, etc...
but i can't open port 465 for smtp.

i am using the PEAR SMTP library to send mails via smtp from php scrips.the SMTP server i'm using is from gmail and uses:
```

Port for TLS/STARTTLS: 587
Port for SSL: 465

```

i tried the following:
```

ufw allow 465
ufw allow 465/tcp
ufw allow 465/udp
ufw allow 587
ufw allow 587/tcp
ufw allow 587/udp

```
but my script still can't connect to the SMTP server.i'm 99% sure that is firewall related because when i turn it off everything works perfectly.

pls help :)

thank you.

Edit:

forget it, no firewall.i spent 6 hours trying to configure it and still no result.

---

