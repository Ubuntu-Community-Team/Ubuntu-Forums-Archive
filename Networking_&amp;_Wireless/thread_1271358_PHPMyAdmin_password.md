---
title: "PHPMyAdmin password?"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by fredbird67 on 2009-09-20
OK y'all, I've got a real dumb question here:

I'm trying to get things set up to create a CMS-based website for my church.  I'm downloading the components of the LAMP server setup that comes from Synaptic, where the web server directory is "/var/www/".  I can install Apache, MySQL, and PHP just fine.  But does ANYBODY know the password for PHPMyAdmin whenever I'm prompted for it in Synaptic?  I've tried leaving it blank, I've tried my login password, I've tried heaven only knows what else, and NOTHING seems to work.

Why on God's green earth is it asking me a question I can't come up with the correct answer to, on a computer I rightfully OWN, of all things?  This wouldn't be a bug in MySQL or PHPMyAdmin, would it?

Thanx in advance,
Fred in St. Louis

---

### Post by i.r.id10t on 2009-09-20
It is to create a password for the root mysql user (at least, apt-get asks for one, I don't do synaptic).

Access phpmyadmin from localhost (and i'd lock it down in apache so that it only listens to localhost - look at the /docs directory directives sample in the default httpd config file, it will tell you how to make that one directory only avaialble from certain hosts) and login with hte username root and the root password you created for mysql (serperate from your regular root password), then create a user and give that user rights.  The specify localhost, that user, that password, and the db name you created and gave permissions on.

---

### Post by fredbird67 on 2009-09-21
i.r.id10t, no offense, but I don't think you understood my post.

BTW, going elsewhere on here, I found that I needed to set up what I think is a hard link in /var/www/phpmyadmin that points to /usr/share/phpmyadmin, and that has, if nothing else, gotten phpmyadmin's main page to show up when I type "localhost/phpmyadmin" into my browser, so I am getting somewhere.

However, the original problem remains.  I **still** have **no clue whatsoever** just what the password is.  When I try all but one of the username and password combinations I've tried so far, I get the following error messages:  "#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)" and "Connection for controluser as defined in your configuration failed."

**However...** when I tried entering "root" for the username and leaving the password blank, I got an "access denied" message.  So as it turns out, it **did** respond, contrary to what the previous error message said.

Therefore, even though I finally got PHPMyAdmin installed, the original question still remains...what's the username and password?

---

### Post by fredbird67 on 2009-09-21
OK, I've figured it all out, y'all.  I found out how to change the MySQL password (I think it was something like "sudo dpkg-reconfigure mysql-server-5.1" or something like that) and now I'm in! :guitar:

---

