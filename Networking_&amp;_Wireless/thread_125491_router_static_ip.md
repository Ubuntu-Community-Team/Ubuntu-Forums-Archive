---
title: "router /static ip"
date: 2006-02-04
forum: Networking &amp; Wireless
---

### Post by Hotchilli on 2006-02-04
Over the past few weeks I have noticed that my internet 
download speed is only 127kbs and te connection speed is 1000kbs

I have noticed in my network properties that dns server is
 192.168.1.2    which is my router.

sometimes internet is slow and also terminal connection keeps
timeing out. but if I change the dns server in my network
properties to my ISP primary dns (212.23.6.100) everything
is fine terminal works download speed excellent.

So whay is my router causing these problems?

hc;) ;)

---

### Post by stream303 on 2006-02-04
This is pretty typical of soho routers with internal dns services.  Easy to fix.

Two different ways to go about it:

1) You can go into your router's setup page and enter your isp's dns address.  After a reboot (or bringing your interface down and up again, you'll be fine).

or

2) If you don't want to change your router configuration, you can edit
**/etc/dhcp3/dhclient.conf**  (sudo gedit /etc/dhcp3/dhclient.conf)

Find the line that starts with "request".
Just before this line, add the following:

**prepend domain-name-servers 212.23.6.100;**

(do not use a # at the beginning, write servers with an s at the end, and don't forget the semicolon at the end)

Now you can either reboot, or more elegantly bring your ethernet interface down and up again from the terminal:

sudo ifdown eth0
sudo ifup eth0

What is happening is that every time you get a new lease, or reboot, **/etc/resolv.conf** is overwritten by the dhclient process, and it picks up only the first dns server inside your router, and not your isp's dns servers.  Some soho routers do this.

Should be good to go from here on out...

---

