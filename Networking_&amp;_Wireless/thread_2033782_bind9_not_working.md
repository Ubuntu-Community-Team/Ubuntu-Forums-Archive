---
title: "bind9 not working"
date: 2012-07-26
forum: Networking &amp; Wireless
---

### Post by computerboy on 2012-07-26
Hi everyone,


I've recently been trying to get a website up and running that's an information page for my Minecraft server (if you don't know what Minecraft is, that's fine) and bind9 doesn't seem to be working for me, so I was hoping someone here could help me out. Also note that I typed in my ip that the webpage I'm hosting on apache is on, and it worked fine. But I still don't know if apache just isn't configured with DNS correctly or something, so here's the config file for the website that's in /etc/apache2/sites-available: 


```
<VirtualHost *:1353>
        ServerAdmin webmaster@localhost

        ServerName www.techsmcserver.net # <- the domain name for the website that I want to use for my website of cour$

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

```

And here's the bind9 db config file that I named "db.www.techsmcserver.net": 


```
 www.techsmcserver.net
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     www.techsmcserver.net. techboy291.techsmcserver.net. (
                              5         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
www.techsmcserver.net   IN      A       192.168.1.104
;
@       IN      NS      www.ns.techsmcserver.net.
@       IN      A       192.168.1.104
@       IN      AAAA    ::1
ns      IN      A       192.168.1.104
techsmcserver.net       IN      CNAME   www.techsmcserver.net

```


Here's the config file named "named.conf.local": 


```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "www.techsmcserver.net" {
        type master;
        file "/etc/bind/db.www.techsmcserver.net";
};

zone "1.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/db.192";
};




```


Okay, this is the last one, I named this one "db.192": 


```
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     www.ns.techsmcserver.net. techboy291.techsmcserver.net. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.
1.0.0   IN      PTR     www.ns.techsmcserver.net.

```


Also, I read the Apache tutorial here: [https://help.ubuntu.com/12.04/serverguide/httpd.html#http-configuration](https://help.ubuntu.com/12.04/serverguide/httpd.html#http-configuration)

and read the bind9 tutorial starting from this part in the page: [https://help.ubuntu.com/12.04/serverguide/dns-configuration.html#dns-primarymaster-configuration](https://help.ubuntu.com/12.04/serverguide/dns-configuration.html#dns-primarymaster-configuration)


Thanks for the help in advance!

---

