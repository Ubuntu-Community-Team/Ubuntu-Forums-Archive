---
title: "Mono asp page ask for download"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by jmarcs on 2010-10-25
Hi all.

I installed Mono on Lucid and I am a newbye on it.

I put an asp page with only that line:
<% Response.Write("Hello World"); %>

I put it on a directory accessed on localhost and the page is displayed. So that's means that Mon is running.

I also put it in a site directory which is accessed by the web by a DynDns redirection on port 8081 (my provider is locking port 80). So the site monrendezvous.dynalias._com_ is redirect to  monrendezvous.dynalias._net_:8081

The problem is that, when trying to access the page from the web it is asking to download it instead of displaying.

There is my Apache2 vhost file:

<VirtualHost *:8081>
  ServerName monrendezvous.dynalias.net
  ServerAlias monrendezvous.dynalias.com
  ServerAlias [www.monrendezvous.dynalias.com](www.monrendezvous.dynalias.com)
  ServerAdmin [email]admin@monrendezvousrmatique.com[/email]

  DocumentRoot /var/www/monrendezvous/public_html

    MonoPath default "/usr/bin/mono/2.0"
    MonoServerPath default /usr/bin/mod-mono-server2
    AddMonoApplications default "/:/var/www/monrendezvous/public_html"
    #<location />
    <location /var/www/monrendezvous/public_html>
        AddHandler mono .aspx .ascx .config .axd .asax .ashx .asmx
        MonoSetServerAlias default
        SetHandler mono
    </location>
        
    <Directory /var/www/monrendezvous/public_html>
        Options Indexes FollowSymLinks
        AllowOverride None
        Order allow,deny
        Allow from all
    </Directory>

    Alias /php/ "/var/www/monrendezvous/php/"

    <Directory "/var/www/monrendezvous/php">
        AllowOverride None
        Options Indexes MultiViews FollowSymLinks
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/monrendezvousError.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/monrendezvousAccess.log combined
</VirtualHost>

Somebody have an idea ?

Thanks for your help.

Jean-Marc

---

