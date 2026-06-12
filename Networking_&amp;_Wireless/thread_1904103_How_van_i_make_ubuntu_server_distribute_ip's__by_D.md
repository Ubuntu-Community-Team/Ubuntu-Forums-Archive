---
title: "How van i make ubuntu server distribute ip's  by DHCP ?"
date: 2012-01-04
forum: Networking &amp; Wireless
---

### Post by kmabuntu on 2012-01-04
Hi All
I'm new in Ubuntu world and I want my ubuntu server distrebute IPs to another machine through DHCP .
any one help me to know how ?
thanks too much

---

### Post by sj1410 on 2012-01-04
you have to install dhcp server on your ubuntu system, follow this steps

```
sudo apt-get install dhcp3-server
```

edit the config file

```
sudo nano /etc/dhcp3/dhcpd.conf
```

example:
```

default-lease-time 600;
max-lease-time 7200;

option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;
option domain-name-servers 192.168.1.1, 192.168.1.2;
option domain-name &#8220;yourdomainname.com&#8221;;

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.10 192.168.1.200;
}
```

save and exit the file and restart the daemon

```
sudo /etc/init.d/dhcp3-server restart
```

---

### Post by kmabuntu on 2012-01-04
Hi SJ
thanks for ur replay 
but i installed the ubuntu GUI desk top how can i get the shell to write this commands ?
plz forgive me i'm very new in ubuntu world 
thanks again

---

### Post by sj1410 on 2012-01-04
Application--Accessories--Terminal will open the gnome-terminal where you can type the commands. You can also use System--Administration--Synaptic Package Manager to install the dhcp server.

---

### Post by kmabuntu on 2012-01-04
thank you so much

---

### Post by sj1410 on 2012-01-04
you can mark this thread as solved using the thread tools.

---

