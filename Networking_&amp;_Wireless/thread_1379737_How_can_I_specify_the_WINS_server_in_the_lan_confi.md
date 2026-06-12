---
title: "How can I specify the WINS server in the lan configuration?"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by vocs on 2010-01-12
Hello,

I'm trying to configure my ubuntu 9.10 to access a lan. In the gnome network manager I can find all the blanks to fill with the ip, subnet mask, gateway and dns, but I can't understand how I can specify the wins server ip. Any suggestions?


Thank you

---

### Post by adam814 on 2010-01-12
It won't matter if you're not running Samba on the Ubuntu machine.  If you are there's a line for it in /etc/samba/smb.conf

---

