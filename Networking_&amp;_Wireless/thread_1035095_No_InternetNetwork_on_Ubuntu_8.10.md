---
title: "No Internet/Network on Ubuntu 8.10"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by asmgx on 2009-01-09
Hi
I have installed Ubuntu 8.10 on Virtual PC (Vista)
it is working fine, except 1 thing
i cant connect to the internet.

I am totally new on Ubuntu and dont know what to do to get internet on Ubuntu

anyone can help?

---

### Post by anystupidname on 2009-01-09
Obviously, first make sure virtual networking for VPC is functional.

# means run as superuser

# ifconfig
to find out what your IP is.
# nano /etc/network/interfaces
if you want to set a static IP (or just use the network manager in "systray")

if you are failing to get an IP or connectivity
# /etc/init.d/networking restart
to restart networking
# dmesg
to check what is going wrong

---

### Post by superprash2003 on 2009-01-09
in windows do you require a dialer to connnect to the internet or does internet work as soon as you switch on your modem? in the ubuntu terminal type ifconfig and post output

---

### Post by asmgx on 2013-02-22
thanks it worked

---

