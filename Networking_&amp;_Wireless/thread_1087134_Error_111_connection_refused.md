---
title: "Error 111 connection refused"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by co789 on 2009-03-04
I have been using Ubuntu Desktop for almost a year now without any problem I couldn't sort out (might say 'long time reader, first time poster), but now I need to install a LAMP server on 8.10 server.  Sounds simple--sudo tasksel install lamp-server, or use apt-get.  Neither work.

I should add that I have 8.10 installed on a VMware server.

When I run "sudo tasksel" tasksel opens and I have the option to install ONLY "Basic Ubuntu Server".  I have no other options.

sudo apt-get update gives me several errors, all of format:

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/](http://security.ubuntu.com/ubuntu/dists/) ... Could not connect to <my IP> (111 Connection refused).

Here's more to the riddle:
I can ping computers on this network.  Computers on this network can ping me.  I can ping google.com using "ping <outside ip address>" but cannot ping google.com, [http://www.google.com](http://www.google.com), or [www.google.com](www.google.com) (ie, have connectivity but cannot get to DNS).  Apparently, I have a connection but cannot use it?

I followed the instructions to change from a DHCP to static IP address at 

[http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)

I am pretty sure my values in /etc/network/interfaces are correct.  I've spent quite some days trying to fix this, and have had a second brain try to figure it out.  I just don't know.

From reading other posts for solved problems, it seems like the entire Ubuntu community is G and can solve any problem without even turning their brains on, so thanks erbody for all the posts I've browsed in the past.  I'm writing under an assumed name so that no one will ever find out I needed to post because I couldn't get a server to connect to the Internet.  Sheesh.

---

### Post by co789 on 2009-03-19
OK, the answer is this page:

[https://help.ubuntu.com/community/VMware](https://help.ubuntu.com/community/VMware)

Apparently, this has been a problem for a lot of people for quite some time.  As a result, there are an incredible amount of Frankenstein fixes out there, but this is how you get it working correctly.  Somehow, I managed to find this page last of all...if only I found it first of all.

So if you are having any trouble with installing Ubuntu on a VMWare server, disregard all other advice and go to the page above.  That is how to install Ubuntu on a VMWare server.

---

