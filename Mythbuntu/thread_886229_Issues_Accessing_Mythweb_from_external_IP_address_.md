---
title: "Issues Accessing Mythweb from external IP address Mythbuntu 8.04"
date: 2008-08-10
forum: Mythbuntu
---

### Post by nigel502 on 2008-08-10
Hey all . . . 

I've been having issues with my 8.04 mythbuntu box. I'm using / used the mythbuntu GUI mythweb security setup to get me started in mythweb - which I'm now starting to regret.

I have been unable to access my box from an external IP - work, new cell phone . . . etc. As long as I'm accessing the machine from my LAN ie 192.168.1.xxx I'm good to go. 

Externally - I can access other sections of my box through these devices and using a .htaccess file, but for the life of me I can't figure out how or where the digest or access files get stored for the Mythbuntu / Mythweb Security and how to modify the settings to allow it to be viewed externally.

Thanks,

---

### Post by Lindsay.Mathieson on 2008-08-10
So does your mythbox have a public IP or does your router forward port 80 to it?

---

### Post by nigel502 on 2008-08-11
Yes my router is set up to forward all traffic on 8080 as I've modified my ports.conf

I can see files externally that I've placed in my /var/www/ directory, I can even access other subdirectories that I've setup with .htaccess permissions. However I can find no data on how the Mythbutu Mythweb permissions are handled.

---

### Post by newlinux on 2008-08-11
Hmm, all I had to do was forward my port from my router to the mythweb machine's http listening port.

I am no apache expert, but for the permissions, maybe looking at:
/etc/apache2/sites-available/mythweb.conf

will point you in the right direction.

---

### Post by nigel502 on 2008-08-12
Is it possible for you to post your mythweb.conf. this is how mine reads:

   AuthType           Digest
    AuthName           "MythTV"
    AuthUserFile       /etc/mythtv/mythweb-digest
    Require            valid-user
    BrowserMatch       "MSIE"      AuthDigestEnableQueryStringHack=On
    Order              allow,deny
    Satisfy            any

Is that the only relevant section? This is mythbuntu 8.04 right out of the box

---

### Post by newlinux on 2008-08-13
That is exactly how that section in my mythweb.conf looks. What error do you get when you access it externally? Perhaps you should setup an .htaccess file in your mythweb directory - it should override the mythweb.conf file. See if putting the same security there as you do in your other directories works.

---

### Post by nigel502 on 2008-08-13
Thanks for your help - I figured it out - using a htaccess file I was able to get it.

Turns out that some setting in apache doesn't let digest level security to work w/ non 192.168.xxx ip's, I can get basic working however.

For others who might be looking into this in the future- create a file in the specified directory called:
.htaccess 

File data:
AuthUserFile /var/www/mythweb/.htpasswd
AuthName "Mythweb"
AuthType Basic
Require valid-user

Then use this command to create the .htpasswd file
sudo htpasswd -c .htpasswd #username


Thanks all

---

### Post by neutron68 on 2009-10-03
I'm running Mythbuntu 9.04 and I'm trying to do the same thing - change the apache2 port to something other than 80 - to be used from my LAN and from outside my LAN (from work).
I do have a password entered into the Mythtv Control Center, which works fine when the port is 80.

I edited the /etc/apache2/ports.conf file to:
```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 8282

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>
```
After I restart the apache2 server and try to log into the Mythweb page with XXX.XXX.XXX.15:8282 (from inside my LAN), I get an error in the web browser:
> Not Found

The requested URL / was not found on this server.

Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.2 with Suhosin-Patch Server at XXX.XXX.XXX.15 Port 8282

Given that I have a error message from the Apache server, it appears the apache2 server is working and getting the page request.  

Now, if I change the ports.conf file back to say "Listen 80", and restart the apache2 server, then mythweb works again!

Does anyone see enough clues here to see what is missing?

Cheers!
Eric

---

### Post by neutron68 on 2009-10-06
I tried a few things and Mythweb works with port 8282, now.
  
After each step shown, I restarted the apache2 server with a "sudo /etc/init.d/apache2 restart" and tried to log into the Mythweb server.  
It did not work until I completed step 3 below.

1.  I changed the /etc/apache2/ports.conf file so it looks like this:
```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:8282
Listen 8282

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>
```

2. I edited the first line of the /etc/apache2/sites-enabled/000-default file to look like this:
```
<VirtualHost *:8282>
```

3.  I changed the /etc/apache2/sites-enabled/000-default filename to /etc/apache2/sites-enabled/default-mythbuntu

After step 3 and a restart of the apache2 server, I could log into Mythweb via port 8282.

I hope this helps someone else!
Eric

---

### Post by metu71 on 2009-11-11
Thanks a lot! I wanted to use another port for mythweb and with your guide I had it working with the first attempt.

---

