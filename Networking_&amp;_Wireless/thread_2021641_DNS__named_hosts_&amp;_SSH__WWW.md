---
title: "DNS / named hosts &amp; SSH / WWW"
date: 2012-07-09
forum: Networking &amp; Wireless
---

### Post by simoninman on 2012-07-09
Good evening all,
I have been struggling to find the answer to this in the past few days and any help would be greatly appreciated.

I am currently a student and new to web hosting and servers.
I have set up a server at home running ubuntu 12.04 server 64bit and i have set this up as a web server linking my domain name to my static ip address and then using port forward on my router to link it to that server.

My issue is I am wanting to run 2 different sites within the www folder using subdomains if possible and also have an external link to ssh and ftp. I have tried changing the /etc/apache2/sites-available/ and hosts.conf along with using a2ensite but when connecting to my domain it will only allow me to connect to the first site and nothing else.

does anybody know where i can go to get more information on this or if it is even possible?

thank you.

---

### Post by SeijiSensei on 2012-07-09
If you're okay with URLs like [http://www.example.com/site1/](http://www.example.com/site1/) and [http://www.example.com/site2/](http://www.example.com/site2/), that's the easiest way to do things.  Just put each site's files in /var/www/site1 and /var/www/site2.

If you're committed to URLs like [http://site1.example.com/](http://site1.example.com/) and [http://site2.example.com/](http://site2.example.com/), then you need to do the following:

1) In your DNS records add A or CNAME records so that site1.example.com and site2.example both point to your IP.

2) In Apache, you'll need to learn how to set up separate virtual host definitions.  On Ubuntu the standard solution is create a separate file in /etc/apache2/sites-available/ for each site that looks like this:

```

<VirtualHost *:80>
    ServerName site1.example.com
    DocumentRoot /path/to/site1/files
    [other options as relevant]
</VirtualHost>

```

You then use the command a2ensite to activate each site.  See the [Server Guide](https://help.ubuntu.com/12.04/serverguide/httpd.html) for more details.

---

### Post by simoninman on 2012-07-09
@SeijiSensei Thank you very much, thats so simple.

---

