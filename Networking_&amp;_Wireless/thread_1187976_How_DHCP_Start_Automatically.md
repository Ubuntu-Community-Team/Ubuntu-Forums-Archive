---
title: "How DHCP Start Automatically"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by mthalis on 2009-06-15
I want to start DHCP server when machine start, in my machine 
system -> administration -> services -> DHCP server is marked,
but after rebooting machine, DHCP server not start.
I used "/etc/init.d/dhcp3-server status" it gave "Status of DHCP server: dhcpd3 is not running"

This is my dhcp.conf file
----------------------------------------
ddns-update-style interim;


subnet 192.168.20.0 netmask 255.255.255.0 {
 #       option routers                  192.168.101.1;
	 option routers			192.168.20.254;  
         option subnet-mask              255.255.255.0;

         option domain-name              "example.com";
         option domain-name-servers       203.115.0.18;

        option time-offset              -18000;     # Eastern Standard Time

#	range 192.168.20.1 192.168.20.254
	range dynamic-bootp 192.168.20.1 192.168.20.24;
        }
-------------------------------------------

please help me start DHCP server start when machine on. My machine is Ubuntu 9.04 Desktop version.

---

### Post by Iowan on 2009-06-15
You have an interface in the 192.168.20.0 subnet?

---

### Post by Iowan on 2009-06-15
You have an interface in the 192.168.20.0 subnet?  Dunno if it still works this way, but on my Breezy server, I can use **runlevel** to check what level my server is running (mine is runlevel 2), then check *ls /etc/rc2.d* to verify that there is a start script for DHCP - in my case it's```
S40dhcp3-server
```

---

### Post by mthalis on 2009-06-15
yes, it was there. what is the next step?

---

### Post by MaindotC on 2009-06-16
If you look at:
```

ls /etc/rc2.d

```
You'll see a list of applications that are included in this directory.  There should be a README file in that directory - read it.

---

### Post by Iowan on 2009-06-16
If you manually start the server (/etc/init.d/dhcp3-server start) - does it actually start? If not, there may be a configuration file problem. You have some options I'm not familiar with - but that certainly doesn't make them wrong...

---

### Post by mthalis on 2009-06-16
yes I can manually start it, I did same way in Ubuntu server 9.04, it worked perpectly.

---

### Post by Iowan on 2009-06-16
What are results of **ifconfig -a** on the server?

---

### Post by mthalis on 2009-06-16
It displaied both network card discription properly.
I formated desktop version and use server version. but still do not know what is wrong.

---

### Post by jhannah on 2009-06-16
I would also recommend checking /var/log/syslog. Try rebooting and then running the below command:

```
grep dhcpd /var/log/syslog
```That is assuming you do not have syslog configured to redirect messages from dhcpd to another file.

Lastly, just for clarification, in your original post you were referencing the config from /etc/dhcp3/dhcp**d**.conf correct?

---

### Post by MaindotC on 2009-06-17
Do you have your IP address set statically?

---

### Post by Iowan on 2009-06-17
What are the IP addresses on the interfaces?

---

### Post by mthalis on 2009-06-17
I have 2 network card. one connect to internet other connect to local network,  local network card issue dhcp to local network.
internet IP 192.168.101.232
local IP    192.168.20.254

---

### Post by Iowan on 2009-06-18
Have you tried switching the cables to see if they might be reversed by designation? (What should be going to internet is actually going to local net, and what should be local is connected to internet.)

When you manually start DHCP - it DOES show as running?

---

