---
title: "Web Hosting/Deployment Problem With Ubuntu But Not With Windows"
date: 2011-11-15
forum: Networking &amp; Wireless
---

### Post by OtagoHarbour on 2011-11-15
I have dual booted my home computer with Ubuntu 11.04 and Windows XP.  I have a static IP address that I have registered to my site name with 1and1.  I have no problem deploying my web site with Windows XP and it can be viewed anywhere, including on wireless devices.  So my port forwarding seems to be fine.

With Ubuntu, I put index.html and index.php in both /var/www and in a newly created directory /var/www/htdocs.  I even did 
```
iptables --flush
```and rebooted the PC.  I can access files in /var/www/ from computers on my LAN, but when I try to access my web site, even from a home computer,  I get the following message.

```
The connection has timed out    
        
             The server at mywebsite.com is taking too long to respond.
   
  The site could be temporarily unavailable or too busy. Try again in a few
    moments.
  If you are unable to load any pages, check your computer's network
    connection.
  If your computer or network is protected by a firewall or proxy, make sure
    that Firefox is permitted to access the Web.
```Any assistance with this would be greatly appreciated,
Peter.

---

