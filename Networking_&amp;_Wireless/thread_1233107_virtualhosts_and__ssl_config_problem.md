---
title: "virtualhosts and  ssl config problem"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by pdc124 on 2009-08-06
having spent most of the morning fiddling with this i think i need some 
advice : 

ive got a server which currently has 2 http:// virtual hosts configured  and works

i want to add an https://  option for one of them .

you can only have one SSL/https connection per IP address ( unless you use a mod_rewrite workaround). 
So can I have 2 vhosts listeingin on port 80 [http://vhost1](http://vhost1) and  http:/vhost2  and also one of them listening on 443 

[https://vhost1](https://vhost1) ?


 in 000-default
NameVirtualHost *
#NameVirtualHost *:80
#NameVirtualHost *:443
<VirtualHost *:80>

and /etc/apache2/sites-enables/ssl 
#NameVirtualHost *
<VirtualHost *:443>
        ServerAdmin webmaster@localhost

> root@server:/etc/apache2/sites-enabled# /etc/init.d/apache2 start
 * Starting web server apache2apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[Thu Aug 06 12:31:29 2009] [error] VirtualHost *:443 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Aug 06 12:31:29 2009] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Aug 06 12:31:29 2009] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Aug 06 12:31:29 2009] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Aug 06 12:31:29 2009] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
      
and it fails to start 

if i do it like this  it also fails to start 
> NameVirtualHost *:80
NameVirtualHost *:443
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
     Servername .....
   it does this 

root@server:/etc/apache2/sites-enabled# /etc/init.d/apache2 restart
 * Restarting web server apache2apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
httpd (no pid file) not running
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                                                                                   [fail]
root@server:/etc/apache2/sites-enabled#
                                                         

so is it possible without needing the mod_rewrite hack , and if so , how ?

---

### Post by pdc124 on 2009-08-15
ive spent a good while sorting this out  - i think ive got it eventually

the problems that needed fixing 

1. once the ssl module is loaded apache wouldnt start - apache error log says it was trying to write to /etc/apache2/logs/ssl_request_log, which didnt exist , so i had to create it 

<VirtualHost *>
needs changing to 
<VirtualHost *:80>

the  ssl virtualhost definition needs to be 

NameVirtualHost *:443
<VirtualHost *:443>
        ServerAdmin webmaster@localhost

All i need to do now is genreate a certificate that matches the domain name.

---

