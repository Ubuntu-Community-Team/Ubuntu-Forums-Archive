---
title: "mythbuntu mythweb security"
date: 2012-02-28
forum: Mythbuntu
---

### Post by ijumpship on 2012-02-28
I need to Access my mythweb internally with security enable,but not have the internal network asking for username and password but is having difficulty with the setup

my internal IP address is 192.168.1.1 - 192.168.1.254
subnet mask 255.255.255.0

I am using mythbuntu 11.10 with IP address 192.168.1.10

I have enable security using the MCC with
 Username  blahblah
 Password  notthisone


I have place the following in /etc/apache2/sites-enabled/mythweb.conf


[I]<LocationMatch "/var/www/mythweb">
  Options Indexes FollowSymLinks
  AuthType Digest
  AuthName "MythTV"
  AuthUserFile /etc/mythtv/mythweb-digest
  Require valid-user
  Order allow,deny
  Allow from 192.168.1.
  Allow from 127.0.0.
  Satisfy any
</LocationMatch>[/I]


However when I go to 192.168.1.10 or 192.168.1.10/mythweb it still ask for the username and password.

I search the web and have done almost everything  these two say but still no dice

-http://www.mythtv.org/wiki/MythWeb#MythWeb_password_authentication

-https://help.ubuntu.com/community/MythWeb

-and I search all the forum instructions(too numerous to list here)

I notice these instructions are older.

Can anyone direct me with a current instruction?

---

### Post by newlinux on 2012-02-28
> **ijumpship said:**
> I need to Access my mythweb internally with security enable,but not have the internal network asking for username and password but is having difficulty with the setup

my internal IP address is 192.168.1.1 - 192.168.1.254
subnet mask 255.255.255.0

I am using mythbuntu 11.10 with IP address 192.168.1.10

I have enable security using the MCC with
 Username  blahblah
 Password  notthisone


I have place the following in /etc/apache2/sites-enabled/mythweb.conf


[I]<LocationMatch "/var/www/mythweb">
  Options Indexes FollowSymLinks
  AuthType Digest
  AuthName "MythTV"
  AuthUserFile /etc/mythtv/mythweb-digest
  Require valid-user
  Order allow,deny
  Allow from 192.168.1.
  Allow from 127.0.0.
  Satisfy any
</LocationMatch>[/I]


However when I go to 192.168.1.10 or 192.168.1.10/mythweb it still ask for the username and password.

I search the web and have done almost everything  these two say but still no dice

-http://www.mythtv.org/wiki/MythWeb#MythWeb_password_authentication

-https://help.ubuntu.com/community/MythWeb

-and I search all the forum instructions(too numerous to list here)

I notice these instructions are older.

Can anyone direct me with a current instruction?

I'm no expert on Apache configs, but I will say my config section for password protection is pretty similar to yours (and does not require a password on my internal IP range but does on externals). The main difference is I have mine inside of <Directory..> </Directory> tags instead of <LocationMatch...></LocationMatch> tags. I believe LocationMatch is meant to do regex matching on URLs. Do you have a Directory directive in your config file as well.

Hope that helps...

---

### Post by ijumpship on 2012-02-28
well I tried this

[I]<Directory "/var/www/mythweb">
 Options Indexes FollowSymLinks
  AuthType Digest
  AuthName "MythTV"
  AuthUserFile /etc/mythtv/mythweb-digest
  Require valid-user
  Order allow,deny
  Allow from 192.168.1.
  Allow from 127.0.0.
  Satisfy any
</Directory>[/I]

and here is the error log


[I**][Tue Feb 28 17:44:30 2012] [error] [client 192.168.1.10] File does not exist: /var/www/favicon.ico**

**[Tue Feb 28 17:44:35 2012][error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico**[/I]


I even tried the username to be "MythTV" in the MCC.

the Access log says a 401 error as I did not put in a password like this

[I127.0.0.1 - - [28/Feb/2012:18:06:08 -0500] "GET / HTTP/1.1" 401 681 "-" "Mozilla/5.0 (X11; Linux i6$
127.0.0.1 - - [28/Feb/2012:18:06:18 -0500] "GET /favicon.ico HTTP/1.1" 404 431 "-" "Mozilla/5.0 (X1$
][/I]

---

### Post by ijumpship on 2012-02-29
Thanks Newlinux for pointing me in a good direction
I am no expert too but I will look at the difference between"<Directory> and <Location>

So here is what worked for me

[I]<LocationMatch .*/mythweb>
 Options Indexes FollowSymLinks
  AuthType Digest
  AuthName "MythTV"
  AuthUserFile /etc/mythtv/mythweb-digest
  Require valid-user
  Order allow,deny
  Allow from 192.168.1.
  Allow from 127.0.
  Satisfy any
</LocationMatch>
[/I]

The Clue at the top of the mythweb.conf file it gives an idea of the format it requires.

This is a policy I adopt some three years ago,when it comes to linux,whereby,I look at what has change and then follow that pattern,but the old head is getting rocky,so it took me a while to see it.

For all the Noob,Linux constantly change and so used the share/doc to catchup.
 
Wish someday they make a link to this user share documents by means of an help on the Menu,so you click and follow.

Well enough said.little White Rum now and I go Sleep.Hope I am some help

---

### Post by nickrout on 2012-03-01
I think if you point /var/www/doc to /usr/share/doc you will have what you want (assuming no linking or permissions dramas).

Than just go to [http://127.0.0.1/doc](http://127.0.0.1/doc)

---

### Post by ijumpship on 2012-03-03
For all who might need the answers  its here

[http://httpd.apache.org/docs/2.2/mod/mod_auth_digest.html](http://httpd.apache.org/docs/2.2/mod/mod_auth_digest.html)

and 

[http://httpd.apache.org/docs/2.2/howto/access.html](http://httpd.apache.org/docs/2.2/howto/access.html)

---

