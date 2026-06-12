---
title: "Changed web server programs -- can't get the new one to start"
date: 2009-09-19
forum: Networking &amp; Wireless
---

### Post by fredbird67 on 2009-09-19
I recently downloaded Apache and everything that goes with it (PHP, MySQL, etc.) from the repositories to develop websites.  I ran into a problem with it when I tried to create a Joomla!-based website for my church.  I looked here on Ubuntu Forums to try to get some database issues sorted out, but everything I ran across involved having the XAMPP web server installed instead, so I decided I'd switch to that, downloaded it, followed all the instructions, and even set it up to automatically start when I started up Ubuntu.

Well, for some strange reason, even after deleting the aforementioned programs from the repositories and installing XAMPP, whenever I type in "localhost" into Firefox, all I'm getting is the default page from the repository installation of Apache (the one where it says "It works!").  What's even more bizarre is that I'm getting that even after going in and manually removing the /var/www directory.  XAMPP's default localhost page isn't showing up at all.  Does anyone know how to **permanently** kill the old Apache server and get localhost to instead go to /opt/lampp/htdocs/index.php?

Thanx in advance,
Fred in St. Louis

---

### Post by fredbird67 on 2009-09-19
Never mind -- after typing that, I tried "localhost/xampp" and I got the XAMPP start page! :-)

---

