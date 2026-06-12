---
title: "resolv.conf gets cleared each reboot"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by tworthy on 2009-12-23
I recently updated two PC's to Ubuntu 9.1 from a previous version. One works fine with no problems. The second one is a different story. Every time the machine is booted and I login, the resolv.conf file is cleaned out and I have no internet access until I manually put the information back in it. I have processed several updates to the code since installation and this keeps happening. Anyone have any ideas about a permanent fix?

---

### Post by puppywhacker on 2009-12-23
I suspect avahi or dhcp keeps updating the resolv.conf with wrong information. As a semi permanent method you can set the access rights of the file to read-only

```
sudo chmod 444 /etc/resolv.conf
```

Although it would be better to find what is killing your resolv.conf and make it stop. So maybe you have to prepend domain-name-server in dhclient.conf or kill avahi one way or another

---

### Post by adam814 on 2009-12-23
Do you have resolvconf installed?  Are you running a DNS server on the machine?

---

### Post by crom.osec on 2009-12-25
You need to edit /etc/network/interfaces and to add dns entries on each interface you need to access internet.
For example, if you are using eth0 to connect to internet you need to add 
on eth0 section the following line:
```

auto eth0
# [...] here are some other settings from eth0
#this is the dns entry for the eth0
dns-nameservers 192.168.1.1 192.168.2.100

```

Of course you must replace the dummy ip values 192.168.1.1, 192.168.2.100 with your real dns entries.

---

### Post by ant2ne on 2009-12-25
I had the similar issue with an OLPC (fedora) and I never did find a fix for it. I just made a quick and dirty boot script that echoed the required settings into /etc/resolv.conf. Probably not the best solution but I only used the device on the one network. And it worked for me.

---

