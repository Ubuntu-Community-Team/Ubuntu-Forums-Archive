---
title: "How to &quot;talk&quot; to virtual Ubuntu 12.04 Nginx server?"
date: 2012-05-19
forum: Networking &amp; Wireless
---

### Post by kramer65 on 2012-05-19
Hello,

I am messing around with setting up a server using Nginx and ISPConfig, mainly to learn about server management. So I installed an Ubuntu 12.04 server in Virtualbox and I followed [this guide]("http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-nginx-bind-dovecot-ispconfig-3") to try to set it up. 

On [page 3 of the guide]("http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-nginx-bind-dovecot-ispconfig-3-p3") I needed to edit /etc/network/interfaces in order to have a static IP address instead of a dynamic one. So I include the following in that file:
```
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        dns-nameservers 8.8.8.8 8.8.4.4
```
Once I did this though, I couldn't get a connection with the internet anymore. I guess this is obvious since I disabled dhcp and tried to manually set the ip-address.

So I did a ifconfig and noted the 'inet addr' (10.0.2.15). I guess this is an internal ip-address on my network or something, but that wouldn't matter since it would be fine if it would just work locally now. So I took that 'inet addr' and inserted it in /etc/hosts so that that file now looks as follows:
```
127.0.0.1       localhost.localdomain   localhost
10.0.2.15       server1.example.com     server1
```
I then proceeded with the guide until [page 4]("http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-nginx-bind-dovecot-ispconfig-3-p4") where it says: "*That's it! Now when you create an nginx vhost, ISPConfig will take care of the correct vhost configuration.*"

So I now simply wanted to see whether I can somehow talk to the server which I just set up. So on my guest OS (also Ubuntu 12.04) I inserted the ip-address which I set before (10.0.2.15) in firefox and waited what would happen. Unfortunately nothing happened and after a while I simply got a page saying that the server on 10.0.2.15 took too long to respond. I then opened Putty and inserted the ip-address there and wayted for a while, but it also ended in a message saying that making the connection took too long.

So could anybody help me out in how I can somehow connect to the server I just installed?


All tips are welcome!

---

### Post by Ms. Daisy on 2012-05-21
It looks to me like the tutorial you followed is for setting up a server that sits on your LAN. It does not seem to address a virtual machine installation.

You'll want to read about networking a virtual machine:

[http://www.virtualbox.org/manual/ch06.html](http://www.virtualbox.org/manual/ch06.html)

Networking in a virtual machine is pretty much done for you through virtual box, but I've never done a static IP.  There's probably a section about it in the virtualbox manual.

---

