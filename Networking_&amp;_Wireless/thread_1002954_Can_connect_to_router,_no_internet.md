---
title: "Can connect to router, no internet"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by europopprincess on 2008-12-05
Hi, everyone, I've got a Sony Vaio laptop that I've recently converted over from XP to Ubuntu 8.1, and I can't seem to get it to connect to the internet (wireless), although it does connect to the router (2wire 2701-HG).  I have a Vista, a Mac, and Wii connected wirelessly, and a wired dual-boot Vista/Ubuntu 8.1 connected to the network; none of which have ever had problems connecting.  I've tried using a wired connection, but it does not recognize the network cable, even though it recognizes the hardware.  I've already disabled ipv6 via /etc/modprobe.d/aliases and /etc/modprobe.d/blacklist, and it lets me connect to the router with 99% signal strength, but does not allow me to connect to the internet.  I've already pinged the router, which is fine, but if I try and ping google, I get "unknown host" message.  I've manually configured the ip address because automatic DHCP did not want to give the computer an address.  The address I gave it is well within the range of the modem, and I have had many other computers on the network than I have now.  I'm not running any firewalls, and am completely stuck on this one.

---

### Post by sleepyjon on 2008-12-05
I believe "unknown host" is a dns problem. Try to ping google using the IP address:

72.14.205.100

---

### Post by europopprincess on 2008-12-23
I tried it, but it still refused to give me anything.  I even decided to try the 8.04 live cd to see if a different version might work, but I ran into the exact same problem.

---

### Post by pdtpatrick on 2008-12-23
You mentioned you are not using wired so wireless it is.. do you have mac filtering on? 
Also is your dns configured properly? check that all your dns packages are installed properly. 

does it currently receive an IP? if so is it a proper IP and not the 169.xx.xx.xx

---

### Post by superprash2003 on 2008-12-24
post output of the following from the terminal
1)ifconfig
2)cat /etc/resolv.conf
3)ping 72.14.205.100

---

