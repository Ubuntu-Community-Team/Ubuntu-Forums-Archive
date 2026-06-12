---
title: "ubuntu 10.10 networking problem"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by Blastnsmash on 2010-12-21
I just installed ubuntu server 10.10 and need to do one of two things: 

1. I want to refer to the ubuntu server by a computer name from other computer on the network. This does not work. No other computer can find ubuntu server by its computer name except ubuntu itself. I can ping by the computer name on the computer itself:

ping UbuntuComputer gets response but on another computer on the same network the computer cannot be found. Note if you use the IP address you can certainly find UbuntuComputer. Basically, from another computer on the same network I can ping the Ubuntu computer by IP but not by computer name, but if I go to the Ubuntu computer itself and ping it by name then it pings successfully. I am trying to ping the Ubuntu computer with a windows machine...that could be the case.

2. So being the case that I cannot get number one to work, I said ok, lets just set a static route then. So here is my primary network interface setup:

#The primary network interface
auto eth1
aface eht1 inet static
   address 10.0.1.137
   netmask 255.255.255.0
   network 10.0.1.0
   broadcast 10.0.1.255
   gateway 10.0.1.1

This works until some unknown time which it sets itself back to 10.0.1.7. If I use the command /etc/init.d/networking restart then it will go back to 10.0.1.137

So, on problem 1 why can't I see the ubuntu server by computer name on other computers on the network? Oh and here is the hosts file:

127.0.0.1 UbuntuComputer localhost.localdomain localhost
::1 UbuntuComputer localhost6.localdomain6 localhost6
127.0.1.1 UbuntuComputer


On problem 2 why the heck does settings a static ip keep getting reset back to dynamic?

This is a fresh install of ubuntu server 10.10 with maverick gui installed.

---

### Post by Blastnsmash on 2010-12-21
I think I figured out what is happening with the static ip resetting. I think the dhcpclient program might be the culprit as per this thread:

[http://ubuntuforums.org/archive/index.php/t-247798.html](http://ubuntuforums.org/archive/index.php/t-247798.html)

I'm going to kill dhcp client and see if it resets tomorrow since the dhcp server is giving out ip addresses that expire in 24 hours.

---

