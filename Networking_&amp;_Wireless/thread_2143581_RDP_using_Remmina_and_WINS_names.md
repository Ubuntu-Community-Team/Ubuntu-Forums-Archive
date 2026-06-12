---
title: "RDP using Remmina and WINS names"
date: 2013-05-09
forum: Networking &amp; Wireless
---

### Post by jamesd3rd on 2013-05-09
I had an earlier post explaining problems with Remmina not being able to connect to a MS Server 2003 box.  That got resolved by using the IP address instead of the NetBios name.  Now I would like to use the WINS name instead of the IP address.  If I use 'connect to server...' to browse the network for a share, that works but if I use the server's name in Remmina it doesn't connect.  Is Remmina designed to use WINS names or is strictly an IP address thing?  I don't have a WINS server.  I would just like to use a lmhosts file to resolve WINS names for now but the few changes I make to the smbd.conf file don't do anything.  I created a lmhosts file in /etc/samba since there wasn't one and just put in one line for the WINS name and the corresponding IP address.  The resolver line in smbd.conf includes lmhosts and it is not commented out.

Shouldn't that be enough for Remmina to resolve by WINS? Do I need a FQDN for the WINS name like <server name>.com or something? It's just a workgroup not a domain and I'm not using a DNS server or a hosts file.  What am I missing?


Thanks.

---

