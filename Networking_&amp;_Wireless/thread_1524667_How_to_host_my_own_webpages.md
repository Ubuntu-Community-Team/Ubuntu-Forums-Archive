---
title: "How to host my own webpages?"
date: 2010-07-05
forum: Networking &amp; Wireless
---

### Post by Atran 0_0 on 2010-07-05
Hi, today I've been reading many threads but found no answer to my question,
How to can I host my own domain by myself for free?

I've installed phpmyAdmin, ehcp, filezilla, mySql, mySql query browser, proftpd, gforge, wordpress, activeperl...

I'm not sure either how to make a domain name for my IP address and how to use dynamic DNS...

1) OK, I've got to admit that I'm a newbie in networking.
2) I'm lost with tons of different programs, I don't know where to start from now, there are many methods. I have made many user names and passwords...
3) What to do? I don't want a local web page, All I want is get my web page on Internet where anyone else can visit it.

Thanks for help.

---

### Post by carsonrose on 2010-07-05
> **Atran 0_0 said:**
> Hi, today I've been reading many threads but found no answer to my question,
How to can I host my own domain by myself for free?

I've installed phpmyAdmin, ehcp, filezilla, mySql, mySql query browser, proftpd, gforge, wordpress, activeperl...

I'm not sure either how to make a domain name for my IP address and how to use dynamic DNS...

1) OK, I've got to admit that I'm a newbie in networking.
2) I'm lost with tons of different programs, I don't know where to start from now, there are many methods. I have made many user names and passwords...
3) What to do? I don't want a local web page, All I want is get my web page on Internet where anyone else can visit it.

Thanks for help.

You still need to install Apache2   (sudo apt-get install apache2) and then put your pages in your /var/www direcrtory... You can host your own site, but you still have to register the domain name and get that pointed to your server........ If you are new to this, I'd suggest googling Apache2 setup....

---

### Post by Atran 0_0 on 2010-07-05
> **carsonrose said:**
> You still need to install Apache2   (sudo apt-get install apache2)I forgot to mention, I already have Apache2.

> and then put your pages in your /var/www direcrtory...OK, so my directory with ordinary html/php files would work.

> You can host your own site, but you still have to register the domain name and get that pointed to your server........How?

> If you are new to this, I'd suggest googling Apache2 setup....OK, I'll search...

---

### Post by bruno9779 on 2010-07-05
There are a few important networking considerations to make, OS independent.

To host anything from your very machine, your domain name needs to be translated to an IP address from a DNS client. This implies that your IP is fixed, or dynamically updated.

99% of ISPs give dynamic public IP addresses. This means that your public IP (external IP) gets changed without you being notified.

This has 2 solutions:

1 (expensive) rent an SDSL line from your ISP, or any other form of fixed IP connection

2 (cheap) get informed about services like dyndns. It routes the traffic to your server, getting updated frequently by a deamon, on your IP changes


Dyndns can be tricky to set-up, feel free to post back

PS: Look for complete howtos to install, referring to the LAMP stack. (Linux Apache2 Mysql Php)

---

### Post by Atran 0_0 on 2010-07-05
I want to change my site, so first I copy the (/etc/apache2/sites-available/default) file and then I change the copy as shown below:

```
<VirtualHost *>

    DocumentRoot /home/ramsin/public_website/www/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>

    <Directory /home/ramsin/public_website/www/vhosts/>
        Options -Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order Allow,Deny
        Allow from All
    </Directory>

    <FilesMatch "access_log|error_log">
        Deny from All
    </FilesMatch>

    ErrorLog /home/ramsin/public_website/log/apache2/error.log
    LogLevel debug
    CustomLog /home/ramsin/public_website/log/apache2/access.log combineddefault

</VirtualHost>
```After that, I place it in another directory, so the new file (default) is in (/etc/apache2/sites-available/mysite/).

In the terminal I write, ```
sudo a2dissite default && sudo a2ensite mysite
```to activate the new site and disable the old one. It works and I restart the apache2, but the same page as before stills coming up! The page is the default ehcp page, and you look that there is a button leading you to the server control panel, and below you read the following: > If you are the owner of this website and were not expecting to see this page, please contact your hosting provider.All I want to know why the same page is showing up when entering [http://localhost/]("http://localhost/?") ?
Thanks...

---

### Post by Atran 0_0 on 2010-07-05
> **bruno9779 said:**
> 2 (cheap) get informed about services like dyndns. It routes the traffic to your server, getting updated frequently by a deamon, on your IP changes
I google it, and I see many websites offering that service. I should sign up, and you can get it free or you have to pay little money. Which website(s) are you recommending? Is the free 'sign-up' enough if I want a website for non-commercial use? Or is it more convenient if I pay a little?...

---

### Post by =CrAzYG33K= on 2010-07-05
First things first..

Did you even register a domain with a provider? 
OR - Are you using a solution from a free web-hosting provider?

---

### Post by Atran 0_0 on 2010-07-05
> **=CrAzYG33K= said:**
> First things first..

Did you even register a domain with a provider? 
OR - Are you using a solution from a free web-hosting provider?

No! So you're demanding that I first go to a website and register a domain name, is this free?

---

### Post by Atran 0_0 on 2010-07-05
I've found this: [http://www.freedomain.co.nr/](http://www.freedomain.co.nr/)
You read that it's free, I'll check it. However, your domain name should end with (.co.nr).

---

### Post by =CrAzYG33K= on 2010-07-05
> **Atran 0_0 said:**
> No! So you're demanding that I first go to a website and register a domain name, is this free?

Uhm professional website registration is not free. Something like [www.myname.com](www.myname.com) or [www.myname.org](www.myname.org) is not free

**Examples for registration:**

[=PU.WH.US&origin[page]=Home"]1&1]("http://order.1and1.com/xml/order/Home;jsessionid=00334DA6CFBDE9CD5E7083F55AEB5AA7.TCpfix140a?ucuoId=PUlead%3Ano-server-cross-selling.WH.US-20100706003320-00334DA6CFBDE9CD5E7083F55AEB5AA7.TCpfix140a&site=PU.WH.US&linkOrigin=Home&linkId=hd.log.eue&__frame=_top&linkType=img&__lf=Static&__rd=ac170c23Cj9YTev6PW4nIeJJ3rN9ezy5&origin[site)
[GoDaddy]("http://www.godaddy.com/")


Or you could opt for a free webhost. 
Usually you'd end up with something like [www.myname.site-name.com](www.myname.site-name.com) (not professional-looking), but hey, it's free!

Nice place where you get free webhost providers reviewed :
[http://www.free-webhosts.com/free-php-webhosting.php](http://www.free-webhosts.com/free-php-webhosting.php)

(Since you mentioned you'd be needing PHPMyAdmin, I opted to go with this link!)

---

### Post by Atran 0_0 on 2010-07-05
> **=CrAzYG33K= said:**
> Nice place where you get free webhost providers reviewed :
[http://www.free-webhosts.com/free-php-webhosting.php](http://www.free-webhosts.com/free-php-webhosting.php)
Thanks for that link...

Regardless of domain name,
a) If I use my own computer for hosting a website, then I should register to get a DNS service.
b) If I register to get a website-host provider, I don't need to register for a DNS service, but the host is not my computer.

Which one do you think is more consistent, (a) or (b)?

---

### Post by =CrAzYG33K= on 2010-07-06
> **Atran 0_0 said:**
> Thanks for that link...

Regardless of domain name,
a) If I use my own computer for hosting a website, then I should register to get a DNS service.
b) If I register to get a website-host provider, I don't need to register for a DNS service, but the host is not my computer.

Which one do you think is more consistent, (a) or (b)?

I really did not get what you really mean. But I guess, both statements are consistent. I'd suggest you go with a free-webhost to start out, and yes, you need'nt worry about any DNS records as the webhost solution provider configures everything for you.

---

### Post by bruno9779 on 2010-07-06
[http://www.dyndns.com/](http://www.dyndns.com/)

You can pretty easily set up your website for personal use.

It has a linux client called something like "ddclient". I have successfully set it up (using the free option) a few months back.

You should start with the free option, and see if you really need the advantages of the paying option.

---

