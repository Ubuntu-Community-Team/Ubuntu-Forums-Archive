---
title: "Apache and Server Name"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by rolodoom on 2010-04-11
Hello. I'm Testing Ubuntu 10.04. I installed apache and can't acces from other computer using [http://ubuntupc-name](http://ubuntupc-name)  only can access using [http://ip_address](http://ip_address).

As the apche server machine is on DHCP address, do I need to put anything somewhere ? 

I've been trying to get static IP address on ubuntu 10.04 but there's no luck

Thanks

---

### Post by Iowan on 2010-04-11
One thing to try: 
In */etc/dhcp3/dhclient.conf*, add the hostname to the "send hostname" line.

---

### Post by rolodoom on 2010-04-11
I changed it but not working.

---

