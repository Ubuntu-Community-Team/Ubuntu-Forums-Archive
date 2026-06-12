---
title: "Installing ldap client on 11.04"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by aroeland on 2011-07-15
Hello everybody,

For some time now I've been trying to find a Linux distribution that works well on all the computers we have at the company I work for. I've tried Debian and that worked fine on most computers but not on all. Now I am testing Ubuntu 11.04 on one computer and it works pretty good except for the LDAP client. I can login, but I can't mount the /home folder. 

To install the LDAP client on Debian I followed a guide I found on the internet. The same website has a guide for Ubuntu 11.04 ([http://www.server-world.info/en/note?os=Ubuntu_11.04&p=ldap&f=2](http://www.server-world.info/en/note?os=Ubuntu_11.04&p=ldap&f=2)) as well, but that doesn't work. According to the guide when I type in 

sudo apt-get -y install libnss-ldap libpam-ldap ldap-utils  

the computer should ask for LDAP account for root and the root password, but it never does. I tried to add the root name in /etc/ldap.conf and the password in /etc/ldap.secret, but this doesn't work.

I tried to (re-)install libnss-ldap, but it gives the following message:
update-rc.d: warning: libnss-ldap start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (none)

In fstab I added the following line to mount the /home folder to the server. 
192.168.0.6:/home       /home   nfs     defaults        0       0

Can anybody help me to solve this problem?

Thank you for reading :-)

Best,
Arnoud

---

