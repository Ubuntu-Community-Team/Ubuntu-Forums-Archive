---
title: "Mythweb 0.20.2 from Mythbuntu not accessible..."
date: 2007-09-02
forum: Multimedia &amp; Video
---

### Post by pepsi_max2k on 2007-09-02
Hey I've just installed the latest 0.20.2+fixes debs from mythbuntu's repo, and I can't access mythweb anymore. Browsing to 127.0.0.1 I see the normal apache2-default/ folder link but the usual mythweb one isn't there anymore, although in /var/www I have a mythweb folder symlink to /usr/share/mythtv/mythweb which contains all the mythweb stuff. 

Any ideas what's up / how to fix? All I did during install was chose a username / password when it asked. I don't have to go set that up in an apache config file somewhere aswell do i? Thanks.

**UPDATE:** created my own link to /usr/share/mythtv/mythweb which shows up fine along with the apache folder, but then browsing to it then to mythweb.php shows the following:

> Database Setup Error

The database environment variables are not correctly set in the
included .htaccess file. Please read through the comments included
in the file and set up the db_* environment variables correctly.

Some possible solutions are to make sure that mod_env is enabled
in httpd.conf, as well as having followed the instructions in the
README about the AllowOverride settings.


might be the cause of the problem?

**UPDATE 2:** Ok added

<Directory /var/www/html/mythweb>
  Options FollowSymLinks
  AllowOverride All
</Directory>

to apache2.conf, restarted apache, mythweb worked fine and is now visible in the main folder list. strangely a reboot initially didn't fix anything. and i've now removed the above code and it still works. :confused: . oh well...

---

