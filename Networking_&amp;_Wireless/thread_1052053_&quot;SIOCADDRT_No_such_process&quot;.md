---
title: "&quot;SIOCADDRT: No such process&quot;"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by dphirschler on 2009-01-27
I am trying to set up a server using Ubuntu 8.10 Server Edition.  I am following a guide found here:

[http://www.howtoforge.com/perfect-server-ubuntu-8.10](http://www.howtoforge.com/perfect-server-ubuntu-8.10)

Before setting up static IP, I installed gnome using:

apt-get install ubuntu-desktop
apt-get install gdm

Then I setup static IP by:

nano /etc/network/interfaces

When I run the command /etc/init.d/networking restart, I get:

SIOCADDRT: No such process
Failed to bring up eth0

What happened?  Is this related to the network manager installed with Gnome?

I tried the steps outlined here to no avail:

[http://ubuntuforums.org/showthread.php?t=974382&highlight=SIOCADDRT%3A+process](http://ubuntuforums.org/showthread.php?t=974382&highlight=SIOCADDRT%3A+process)

Can anybody help me here?  


Darryl

---

### Post by dphirschler on 2009-01-27
Never mind.  I gave up and reinstalled Ubuntu Server.  I never really got it off the ground anyway.  I would like to know why Gnome killed it, but for now I am happy just getting the static IP working so I can move on.


Darryl

---

