---
title: "Network stopped working after upgrade xubuntu 9.04"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by filipvermeiren on 2009-09-29
I installed Xubunut 9.04, changed my ip address to fixed ip address in /etc/network/interfaces (see attached). all was fine, internet working, i did an update an now the internet connection is not working, or at least I can ping to the outside, my LAN netwrok connections are working, but firefox and thunderbird does not seem to connect to the internet? Any suggestions?

---

### Post by chili555 on 2009-09-29
> fixed ip address in /etc/network/interfaces (see attached). all was fine,Where is 'attached'? Also, did you remember to populate */etc/resolv.conf*?

---

### Post by filipvermeiren on 2009-09-29
it seems i can't upload these 'invalid' files? I can open them perfectly with 'vim' i changed permisions  (chmod 777) sop they would be readable.
What do you mean by populate /etc/resolv.conf, this file is empty
Is this a change from 8.04? I normally only change interfaces file to have:
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.1.237
netmask 255.255.255.0
gateway 192.168.1.254

---

### Post by chili555 on 2009-09-29
> What do you mean by populate /etc/resolv.conf, this file is emptyIf you use a static IP address, the DNS nameservers will not be supplied by the router; it is up to you to supply them. If you ever connected by DHCP under 8.04, for example during or just after installation, then */etc/resolv.conf* would have been populated. Please do:```
sudo vim /etc/resolv.conf
```Add a single line:```
nameserver 192.168.1.254 
```Proofread, save and close. Now try:```
ping -c3 www.google.com
```If you get ping returns then you should be all set.

Your interfaces file looks just fine.> it seems i can't upload these 'invalid' files?Some system files are not readable by the world. If not, you can always:```
[COLOR="Red"]sudo[/COLOR] cat /your/file
```

---

### Post by filipvermeiren on 2009-09-29
hi Chilli555,

Thanks a million that did indeed do the job!!
Regards,
Filip

---

