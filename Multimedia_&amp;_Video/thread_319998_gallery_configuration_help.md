---
title: "gallery configuration help"
date: 2006-12-16
forum: Multimedia &amp; Video
---

### Post by theorem_hunter on 2006-12-16
i installed gallery using these instructions

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Image_Gallery_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Image_Gallery_Server)

i clicked the link
[http://localhost/gallery/setup/index.php](http://localhost/gallery/setup/index.php)

& i get a error: >>>

404
Not Found

The requested URL /gallery/setup/index.php was not found on this server.
Apache/2.0.55 (Ubuntu) mod_python/3.2.8 Python/2.4.4c1 PHP/5.1.6 Server at localhost Port 80

any sugestions?

---

### Post by Dave54 on 2006-12-16
Did you install Apache HTTP Server for HTTP (Web) Server service, install PHP for Apache HTTP Server, and execute in terminal every command before the link?

---

### Post by theorem_hunter on 2006-12-19
yes, i followed all instructions as in the howto. i got "GNUMP3d" to work & its working thru out the whole network. i cant figure out why im having trouble with gallery

---

### Post by theorem_hunter on 2006-12-21
in the Ubuntu user guide i installed php5. i thought this was the problem & downgraded to version 4. then went thru all the steps until gallery. but no luck :(

GNUMP3d, still works thou :)

should i upgrade my php to version 5? since it wasnt the problem

---

### Post by Jazkal on 2007-01-06
I had the same problem with the ubuntu edgy apt-get package.

Before you restart apache, run this command:

sudo nano /etc/gallery/apache.conf

and un-comment out the Alias line, on line 3.

Then restart apache

---

