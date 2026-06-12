---
title: "Lucid  XAMPP install"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by Ankersman on 2010-11-22
Hope this helps...

Installation of [XAMPP]("http://www.apachefriends.org/en/xampp-linux.html") proceeded smoothly until:  


 ```
sudo /opt/lampp/lampp start
```

resulted in the messages

1. Another MySQL daemon is already running
2. Another web server daemon is already running 
 


Solution to 1; [Geek Lair]("http://anonir.wordpress.com/2010/08/09/ubuntu-lucid-disable-services-from-starting-during-boot/") gives a excellent explanation on how to disable services from starting during boot. Disabling MySql from running at boot solved the problem. 

Solution to 2: This was a little more difficult. I could not find a web server daemon through the above solution 1 procedure, so used Beagle to search for 'apache'. This found an apache2 installation. I used Synaptic Package Manager to remove this installation. Problem solved. 

I rebooted and started lampp again:

 ```
sudo /opt/lampp/lampp start
```

and got a good result 

Starting XAMPP for Linux 1.7.3a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

Hooray!  :)

---

