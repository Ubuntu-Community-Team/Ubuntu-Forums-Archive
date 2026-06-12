---
title: "I broke my DNS -bind9-"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2009-10-27
Im setting up a home server. following this guide.
[http://www.howtoforge.com/perfect_server_ubuntu7.10_p4](http://www.howtoforge.com/perfect_server_ubuntu7.10_p4)

im on "12 DNS Server"

what is wanted me to do was install "bind9"
move it to a new direcory and run it chrooted as user bind.

Im pretty sure i followed the steps exactly, but i cant get bind to start. 

```


                                                                        [fail]
luke@media:~$ sudo /etc/init.d/sysklogd restart
 * Restarting system log daemon...                                       [ OK ] 
luke@media:~$ sudo /etc/init.d/bind9 start
 * Starting domain name service... bind9                                 [fail] 
luke@media:~$ sudo /etc/init.d/sysklogd restart
 * Restarting system log daemon...                                       [ OK ] 
luke@media:~$ sudo /etc/init.d/bind9 start
 * Starting domain name service... bind9                                 [fail] 
luke@media:~$ sudo /etc/init.d/bind9 start
 * Starting domain name service... bind9                                 [fail] 
luke@media:~$ sudo /etc/init.d/bind9 stop
 * Stopping domain name service... bind9                                        rndc: connect failed: 127.0.0.1#953: connection refused
                                                                         [ OK ]
luke@media:~$ su root /etc/init.d/bind9 stop
Password: 
 * Stopping domain name service... bind9                                        rndc: connect failed: 127.0.0.1#953: connection refused
                                                                         [ OK ]
luke@media:~$ su root /etc/init.d/bind9 start
Password: 
 * Starting domain name service... bind9                                 [fail] 
luke@media:~$ 


```

unfortunately it appears Ive also broken the logger.
regardless i have no DNS now. 

thanks for your help.

---

### Post by Iowan on 2009-10-27
I'm kinda fond of **dnsmasq** for DHCP/DNS server - it does a good job of tying the two together so I can ping machines with DHCP address by hostname. It allows static leases, so my network printer and LAMP server always have the same addresses.
You knew this was coming: Why a 7.10 server instead of something LTS (8.04 in particular)?

---

### Post by wlraider70 on 2009-10-27
I'm actually not using 7.10, but i cant find a newer guide.

i see you are using 7.10...


well i have no internet access now, so i have to fix bind first...

---

