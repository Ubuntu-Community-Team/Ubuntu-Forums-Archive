---
title: "Problems with Apache2 and web-hosting"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by gagegannon on 2010-02-07
Hey all, 

So I'm fairly new to the Linux world but I'll try and make my question as clear as possible.

I've recently purchased my own domain name at GoDaddy.com and I'm trying to host this site from my Linux machine.  I've installed the LAMP server and all seems to be working fine.  I've also set up the default site in /etc/apache2/sites-available/default and I can view this site from my Linux machine no problem, but I can't see it from outside of my Linux box.  

I pointed my domain name in GoDaddy to my server IP address and pluged the internet directly into my machine to eliminate any router/port forwarding problems.

here is my current settings by running the following commands:
lsb_release -id
ls -l /etc/apache2/sites-enabled
cat /etc/apache2/sites-enabled/*

```

rick@hal:/$ lsb_release -id
Distributor ID:    Ubuntu
Description:    Ubuntu 8.04.4 LTS
rick@hal:/$ ls -l /etc/apache2/sites-enabled
total 0
lrwxrwxrwx 1 root root 36 2009-03-07 15:10 000-default -> /etc/apache2/sites-available/default
lrwxrwxrwx 1 root root 43 2010-02-07 11:29 ifantasysports -> /etc/apache2/sites-available/ifantasysports
rick@hal:/$ cat /etc/apache2/sites-enabled/*
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
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


NameVirtualHost *:80
<VirtualHost *:80>
        ServerAdmin emailaddresshere@localhost 
    ServerName www.ifantasysports.net:80

        DocumentRoot /var/www/
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


```I've been beating my head against my moniter for about a week now, ](*,) and I'm all out of ideas.  I'm sure it's a simple fix,  I probably just need a fresh set of eyes.

Any help?

---

### Post by mushwars on 2010-02-07
Your problem is not apache. You are in the same situation that I was back in 1999. This is when I first began fooling with servers. I spent weeks trying to figure out why I couldnt see it from the outside but could from [http://localhost/](http://localhost/)

if this is your case you need to do what I did and go into your router and set up portforwarding. It took me weeks to figure out on my own because at the time there was no documentation on port forwarding.

Today there is a resource avaliable as making servers has become more popular.

And here it is.

[http://portforward.com/](http://portforward.com/)

---

### Post by gagegannon on 2010-02-07
Yeah, I thought about that, that's why I unplugged my internet from my router and plugged it directly into in Linux box to eliminate such a problem.

I'm also not viewing my website from [http://localhost](http://localhost)  I'm typing [www.ifantasysports.net]("http://www.ifantasysports.net") into my browser URL, and I AM getting the test page that I've set up, but only from my server machine.  I can't access that same URL from any other machine on the net.  All I get is a "Address Not Found" error in my browser?

---

### Post by pirateghost on 2010-02-07
> **gagegannon said:**
> Yeah, I thought about that, that's why I unplugged my internet from my router and plugged it directly into in Linux box to eliminate such a problem.

I'm also not viewing my website from [http://localhost](http://localhost)  I'm typing [www.ifantasysports.net]("http://www.ifantasysports.net") into my browser URL, and I AM getting the test page that I've set up, but only from my server machine.  I can't access that same URL from any other machine on the net.  All I get is a "Address Not Found" error in my browser?
That would be a DNS issue.

so you bought the domain, configured the domain to point at your ip address, and have tried hooking up your server directly to the modem.
have you made sure you arent running a firewall on your server?

---

### Post by gagegannon on 2010-02-07
So my internet connection goes from my modem directly into my Linux machine with nothing in between.  My domain name points to my linux IP machine address as has for about a week now.  There is no firewall running on my system that I know of.  The only OS currently running is Linux.

---

### Post by pirateghost on 2010-02-07
> **gagegannon said:**
>  My domain name points to my linux IP machine address as has for about a week now. 

your LOCAL IP address or your PUBLIC IP address?

usually when you change from a router to a direct connection the modem will get an entirely new IP address because you have changed the MAC address that was registered to it.

---

### Post by gagegannon on 2010-02-07
The IP address at GoDaddy is the same that is on my machine.  I just re-checked both to make sure.

---

### Post by pirateghost on 2010-02-07
> **gagegannon said:**
> The IP address at GoDaddy is the same that is on my machine.  I just re-checked both to make sure.
Public IP address though right?  not a 192.168.xxx.xxx? or similar?

also note that some ISP's will BLOCK hosting servers on port 80

---

### Post by gagegannon on 2010-02-07
Correct.
```

rick@hal:/var/www$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:9b:27:d2:71  
          inet addr:67.193.190.167  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::221:9bff:fe27:d271/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86579 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73670 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54525167 (51.9 MB)  TX bytes:7723373 (7.3 MB)
          Interrupt:221 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18860 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18860 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3217843 (3.0 MB)  TX bytes:3217843 (3.0 MB)
```Godaddy -> 67.193.190.167

---

### Post by pirateghost on 2010-02-07
who is your ISP?


edit***
based on that IP address it is not a DNS issue, because i cant even get to a webpage from the IP (takes all DNS out of the equation)

---

### Post by gagegannon on 2010-02-07
I'm in the Kingston, ONT area.  My ISP is cogeco which is a sub of Rogers I believe.

I've also tried listening on a different port, (8880 I think it was), but no joy there either?

---

### Post by pirateghost on 2010-02-07
>  While trying to retrieve the URL: [http://67.193.190.167/](http://67.193.190.167/) 
 The following error was encountered: 

[LIST]
[*] ** Connection to 67.193.190.167 Failed **
[/LIST]
   The system returned: 
*    (60) Operation timed out*   The remote host or network may be down.  Please try the request again. 
in your server config can you pull the ```
:80
```off your ServerName directive and restart apache?

---

### Post by gagegannon on 2010-02-07
Done.

---

### Post by mushwars on 2010-02-07
you need to restart apache, you cant just change settings, do this

```
sudo /etc/init.d/apache2 restart
```

---

### Post by gagegannon on 2010-02-07
This is correct.  I made the changes and executed the command.

my config file now looks like:

NameVirtualHost *:80
<VirtualHost *:80>
        ServerAdmin _someemail@place_
    ServerName [www.ifantasysports.net]("http://www.ifantasysports.net")

        DocumentRoot /var/www/
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

---

### Post by pirateghost on 2010-02-07
everything looks correct to me.

no firewall on your system?

can you change the port to 8080?  also change /etc/apache2/ports.conf and add Listen 8080
this should rule out your ISP blocking webserving on port 80

---

### Post by gagegannon on 2010-02-07
If there's a firewall running,I didn't install it?

Made the following changes:

```
rick@hal:/etc/apache2/sites-available$ cat ifantasysports 
NameVirtualHost *:8080
<VirtualHost *:8080>
        ServerAdmin emailaddresshere 
    ServerName www.ifantasysports.net

        DocumentRoot /var/www/
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

rick@hal:/etc/apache2$ cat ports.conf 

Listen *:8080



<IfModule mod_ssl.c>
Listen *:443
</IfModule>
rick@hal:/etc/apache2$ 

rick@hal:/etc/apache2$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                         [ OK ] 
rick@hal:/etc/apache2$ 



```

---

### Post by gagegannon on 2010-02-07
You had mentioned earlier that this may be a DNS problem.  I remember several weeks ago when I was trying to set up apache, that I began setting up the DNS server on my local machine before purchasing my domain name.  Realizing that I would not need such a service one I purchased my domain from GoDaddy, I never finished the initinal setup.  Is there any way I can check to see if my local machine is running its own DNS?

---

### Post by pirateghost on 2010-02-07
by browsing directly to the IP address it would bypass any misconfigured DNS issues.  i still cannot get to the page by IP but i did notice something in your ports.conf file.

my configuration has always been
```

Listen 8080
```
rather than 
```

Listen *:8080
```
but i dont know if that would make any difference at all.

---

### Post by mushwars on 2010-02-07
```

Listen 80

NameVirtualHost *:80

<VirtualHost *:80>
        ServerName dont.fear.jp
        ServerAdmin mushwars@gmail.com
        DocumentRoot "/var/www/localhost/japan/htdocs/"

        <Directory "/var/www/localhost/japan/htdocs/">
            Options Indexes FollowSymLinks
            AllowOverride All
            Order allow,deny
            Allow from all
        </Directory>

        <IfModule alias_module>
            ScriptAlias /cgi-bin/ "/var/www/localhost/japan/cgi-bin/"
        </IfModule>

        <Directory "/var/www/localhost/japan/cgi-bin/">
            AllowOverride None
            Options None
            Order allow,deny
            Allow from all
        </Directory>

        <IfModule mpm_peruser_module>
                ServerEnvironment apache apache
        </IfModule>
</VirtualHost>

```[s]Take a look at my second line you are missing that.[/s]
hrm

**I have it! You renamed your file to ifantasysports you need to go to your httpd.conf and change the file it is looking for to that**

---

### Post by pirateghost on 2010-02-07
> **mushwars said:**
> ```

Listen 80

NameVirtualHost *:80

<VirtualHost *:80>
        ServerName dont.fear.jp
        ServerAdmin mushwars@gmail.com
        DocumentRoot "/var/www/localhost/japan/htdocs/"

        <Directory "/var/www/localhost/japan/htdocs/">
            Options Indexes FollowSymLinks
            AllowOverride All
            Order allow,deny
            Allow from all
        </Directory>

        <IfModule alias_module>
            ScriptAlias /cgi-bin/ "/var/www/localhost/japan/cgi-bin/"
        </IfModule>

        <Directory "/var/www/localhost/japan/cgi-bin/">
            AllowOverride None
            Options None
            Order allow,deny
            Allow from all
        </Directory>

        <IfModule mpm_peruser_module>
                ServerEnvironment apache apache
        </IfModule>
</VirtualHost>

```[s]Take a look at my second line you are missing that.[/s]
hrm
[B]I have it! You renamed your file to ifantasy sports you need to go to  your httpd.conf and change the file it is looking for to that
  
  
[/B]

[s]NameVirtualHost?

he has that[/s]

LOL

edited after you
[B]
httpd.conf should not need editing to reflect the file, because
```
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
```is enabled in apache2.conf
that means that if you have a file located in /etc/apache2/sites-available named fantasysports you need to make sure it is symlinked in /etc/apache2/sites-enabled
[/B]
```
sudo a2ensite ifantasysports
```

---

### Post by mushwars on 2010-02-07
> **mushwars said:**
> **I have it! You renamed your file to ifantasysports you need to go to your httpd.conf and change the file it is looking for to that**

this.

---

### Post by gagegannon on 2010-02-07
I changed the ports.conf to read

```
Listen 80 
```

but there is still no change on my side.

I also tried port 8080 and 8880, nothing there either.

I really appreciate your help in this, I'm sure you can see why I've been having so much difficulty over the last week or so.  From what I can tell everything seems to be set up fine, but I have no idea why things aren't working?  Is it possible there's a corrupt file somewhere, or maybe something that's turned off that should be on?

---

### Post by pirateghost on 2010-02-07
try this:
```
sudo a2ensite ifantasysports
```

---

### Post by gagegannon on 2010-02-07
rick@hal:/etc/apache2/sites-available$ sudo a2ensite ifantasysports 
This site is already enabled!
rick@hal:/etc/apache2/sites-available$ 


:sad:

---

### Post by gagegannon on 2010-02-07
I noticed pirateghost has in his config file....
```

Listen 80

NameVirtualHost *:80

<VirtualHost *:80>
        ServerName dont.fear.jp
        ServerAdmin [EMAIL="mushwars@gmail.com"]mushwars@gmail.com[/EMAIL]
        DocumentRoot "/var/www/localhost/japan/htdocs/"

        <Directory "/var/www/localhost/japan/htdocs/">

```
I have no ServerName declared in my file.  Will this make a difference?  If so, what should the ServerName be?  Anything at all?

---

### Post by mushwars on 2010-02-07
debian changed apache so much that its almost harder to use. Installing from source is the ideal way (but dont do that)

All my ideas have been wrong, I will do a little more thinking, maybe it will come to me.

---

### Post by mushwars on 2010-02-07
> **gagegannon said:**
> I have no ServerName declared in my file.  Will this make a difference?  If so, what should the ServerName be?  Anything at all?

servername is your domain name exactly as you would see it on the web. for instance [www.mushwars.net]("http://www.mushwars.net") or dont.fear.jp or whatever.


edit: you already have it

```
ServerName [www.ifantasysports.net]("http://www.ifantasysports.net/")
```

---

### Post by gagegannon on 2010-02-07
oops!  My bad.

Just getting desperate.

---

### Post by gagegannon on 2010-02-07
ufw has since been installed, however port 80 should be open.

---

### Post by gagegannon on 2010-02-07
Ready to feel like an ***?

Take a look at my config file, specificly the DocumentRoot entry.  

```
NameVirtualHost *:80
<VirtualHost *:80>
         
    ServerName www.ifantasysports.net
    ServerAdmin emailhere
        
    DocumentRoot /var/www/
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
```
Notice it is listed as /var/www/  Looks fine right?  However that line and the <Directory> below it is different from all the other entries, can you see what it is?

It should be entered as ```
DocumentRoot "/var/www"
```Notice the "" at the start and end!  Once this change was made, everything worked like a charm!

Thanks to both of you guys for all your help!  Just knowing that my config was set up properly in the beginning made all the difference.

Cheers! \\:D/

Now how do I mark this thread as solved?

---

### Post by pirateghost on 2010-02-07
strange, i dont have the "" and my sites work fine

```
web:~# cat /etc/apache2/sites-available/default
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
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

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

---

