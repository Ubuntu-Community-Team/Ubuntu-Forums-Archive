---
title: "Create a website name for my IP address"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by venkatraghavang on 2010-03-11
Hi, 
I have 10 systems working on LAN with fixed IP given to all the 10. I have ubuntu installed. "ifconfig" shows my IP on eth0 interface. 

Query : I've my blog at /var/www with Apache installed and it works fine when i give the IP address of eth0 (Not 127.0.0.1). And it works from any system when i give the IP address. 
    * How can i change the IP address to a simple URL. Eg: Instead of [http://173.xxx.xxx.xxx](http://173.xxx.xxx.xxx) to [http://mysite](http://mysite)

I've tried:

1) Adding entry to hosts & configuring httpd.conf in apache. Did not work.
2) I don't want any bind, as it should be accesible only within the LAN.

Experts of Ubuntu Forums, here goes your question..

---

### Post by Barriehie on 2010-03-11
> **venkatraghavang said:**
> Hi, 
I have 10 systems working on LAN with fixed IP given to all the 10. I have ubuntu installed. "ifconfig" shows my IP on eth0 interface. 

Query : I've my blog at /var/www with Apache installed and it works fine when i give the IP address of eth0 (Not 127.0.0.1). And it works from any system when i give the IP address. 
    * How can i change the IP address to a simple URL. Eg: Instead of [http://173.xxx.xxx.xxx](http://173.xxx.xxx.xxx) to [http://mysite](http://mysite)

I've tried:

1) Adding entry to hosts & configuring httpd.conf in apache. Did not work.
2) I don't want any bind, as it should be accesible only within the LAN.

Experts of Ubuntu Forums, here goes your question..

/etc/hosts
```

# IPaddress    HostName    Alias
127.0.1.1    www.mysite.whatever
```/etc/resolv.conf
```

search localhost
```You'll also need to have apache setup for [B][www.mysite.whatever]("http://www.mysite.whatever")

[/B]In /etc/apache2 you've got two sub dir.'s, sites-available and sites-enabled.  For my page I've got the following file for my no-ip.com site in /etc/apache2/sites-available/www.mysite.whatever
```

<VirtualHost *:45826>  # 45826 is my port that no-ip will redirect to, you'll use port 80 for http.
    ServerName www.mysite.whatever
    ServerAdmin barrie@localhost
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

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined
    ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```In /etc/apache2/sites-enabled you then have a symlink of the above file except ending with .conf  You can use **a2ensite** to enable a site in /etc/apache2/sites-available and **a2dissite** to disable sites.  Once I get going on the keyboard I create the links myself.

---

### Post by venkatraghavang on 2010-03-18
Barriehe,
Thanks for your post. I've tried this. The point which i notes is even if i remove all the hosts(and even the file), my apache2 works. I've my company site redirection when i type the IP 127.0.1.1. And it works even after hosts removal.

It still returns "DnsServer returned : Domain name does not exist". What could be the reason?? Could you please help me ??

---

### Post by jrssystemsnet on 2010-03-18
You would have to create the fake domain in the hosts file of EVERY machine within the LAN, in order to have it work by editing host files.  There is no one file that you can edit on the Apache server to make all hosts on the LAN resolve an URL.

---

### Post by venkatraghavang on 2010-03-18
Hi,
Thanks for your response. I've seen it working up in my previous office. I'll reiterate my query again.. 

My Ethernet IP : 172.34.12.22 
I have my default site at var/www/ and it works from all the 10 systems. (If i open the browser and enter as [http://172.34.12.22/](http://172.34.12.22/) )

However, my point is to just add a domain name to that IP address. Any settings which will make:
172.24.12.22 = sitename. So that all 10 systems can access like [http://mysitename/](http://mysitename/)

There is no point of accessing Internet or getting new domain. Just giving a domain name to my IP. 

Any other ways?

---

### Post by lisati on 2010-03-18
> **venkatraghavang said:**
> Hi,
Thanks for your response. I've seen it working up in my previous office. I'll reiterate my query again.. 

My Ethernet IP : 172.34.12.22 
I have my default site at var/www/ and it works from all the 10 systems. (If i open the browser and enter as [http://172.34.12.22/](http://172.34.12.22/) )

However, my point is to just add a domain name to that IP address. Any settings which will make:
172.24.12.22 = sitename. So that all 10 systems can access like [http://mysitename/](http://mysitename/)

There is no point of accessing Internet or getting new domain. Just giving a domain name to my IP. 

Any other ways?

If you don't mind your web site being available for public access, you could set up a name at somewhere like [www.noip.com](www.noip.com) or [www.dyndns.com](www.dyndns.com) and set up forwarding of port 80 on your router to your main machine where apache is running.

---

### Post by jrssystemsnet on 2010-03-18
> **venkatraghavang said:**
> Hi,
Thanks for your response. I've seen it working up in my previous office. I'll reiterate my query again.. 

And I'll reiterate the answer again: **there is no way to do this by editing a file on the Apache server**.  In order to get all machines on your LAN to resolve a hostname to that IP address, you either have to edit the host file on each machine separately, or you have to set up a local DNS server (and make sure all machines on the LAN actually use that DNS server).  Period.  No ifs, ands, or buts.

---

### Post by venkatraghavang on 2010-03-18
Lisati,
Isn't there any other way to solve my issue?? I don't want to make public as i plan to make an internal website for just these 10 systems. I hope there'll be someone out here who faced similar issue..

---

### Post by venkatraghavang on 2010-03-18
Jrssysystem,

Thanks for that.. I guess i'm finding a way.. Can you point out a URL for setting up a DNS server locally??

---

### Post by lemuriaX on 2010-03-18
It's pretty simple to edit the hosts file for all the computers on your LAN...

---

### Post by Barriehie on 2010-03-18
I think you'll have to setup **bind**, say on the hosting machine, and the resolv.conf file on ALL the machines needs to have: (before any other listed name server IP's.
```

search localhost.localdomain
nameserver **ip of machine with bind**

```

---

