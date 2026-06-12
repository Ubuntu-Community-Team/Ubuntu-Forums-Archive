---
title: "Unable to configure DHCP Server on Ubuntu Server 11.04"
date: 2011-08-16
forum: Networking &amp; Wireless
---

### Post by kaustubhg123 on 2011-08-16
Hello,
This is my first thread in the ubuntu forums.
I am installing a new DHCP Server on Ubuntu Server 11.04.
I executed following command:
sudo apt-get install dhcp3-server
Then it said:
invoke-rc.d: initscript isc-dhcp-server, action "start" failed.
Also the directory dhcp3 does not exist in etc.
Has something gone wrong with the installation?
Please help.

---

### Post by zym0sis on 2011-08-16
Hi, no but i guess you are reading posts of the Ubuntu 10.x installation. from 11.04 the information is stored in 

[FONT=&quot]/etc/dhcp/dhcpd.conf[/FONT]

the service is started/stopped like this

 [FONT=&quot]/etc/init.d/isc-dhcp-server start / stop / status[/FONT]
  
the second problem I had was that I needed to find a way to define the ethernet port where DHCP needs to run on ... I have 2 :)

in 10.x this is defined in /etc/default/dhcp3-server but now you need to spec this in /etc/default/isc-dhcp-server

---

### Post by kaustubhg123 on 2011-08-16
> **zym0sis said:**
> Hi, no but i guess you are reading posts of the Ubuntu 10.x installation. from 11.04 the information is stored in 

[FONT=&quot]/etc/dhcp/dhcpd.conf[/FONT]

the service is started/stopped like this

 [FONT=&quot]/etc/init.d/isc-dhcp-server start / stop / status[/FONT]
  
the second problem I had was that I needed to find a way to define the ethernet port where DHCP needs to run on ... I have 2 :)

in 10.x this is defined in /etc/default/dhcp3-server but now you need to spec this in /etc/default/isc-dhcp-server

Thanks for reply.
But I was referring 11.04 documentation from official site here:
[https://help.ubuntu.com/11.04/serverguide/C/dhcp.html](https://help.ubuntu.com/11.04/serverguide/C/dhcp.html)

There they tell that the directory is /etc/dhcp3/dhcpd.conf
Also if I run
/etc/init.d/isc-dhcp-server start
it says command not found.

---

### Post by zym0sis on 2011-08-16
[QUOTE=kaustubhg123;11156945]Thanks for reply.

:) don't always trust the manual ... this is a phrase I had to repeat myself way to often.

well I just installed and got the dhcp server working on my virtual machine with 2 interfaces

I noticed that it is good practice to reboot the server after installing the dhcp.

user@ubdhcp:~$ sudo /etc/init.d/isc-dhcp-server status
[sudo] password for user:
Status of ISC DHCP server: dhcpd is running.

---

### Post by kaustubhg123 on 2011-08-17
Thanks.
it worked!

---

