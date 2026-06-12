---
title: "DHCP on Samba share"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by intermentals on 2010-02-16
I'm swapping from an OpenBSD 4.5 DHCP server to using Ubuntu 9.10

I notice in /etc/samba on Ubuntu there is a file called dhcp.conf with the singular line "wins server =="

There is no corresponding file in OpenBSD so how do I configure this file

Thanks

---

### Post by johnson.d on 2010-02-17
The dhcp.conf file present in the /etc/samba directory is to redirect the clients to WINS server.
In the Single line you have noticed you can add the ip-address of the WINS server (if there is one in the network) as in the following:

wins server = eth0:<ip-address>

---

### Post by intermentals on 2010-02-17
great! - thank you

---

