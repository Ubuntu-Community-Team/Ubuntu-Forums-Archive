---
title: "Create new database on Mythbuntu box"
date: 2008-06-15
forum: Mythbuntu
---

### Post by Medieval Cow on 2008-06-15
Ok, so this might be a little bit of a weird problem, but here it is. I want to set up a new database on my Mythbuntu box. I coded up a little book database in PHP to keep up with my personal library, and it stores the info in a MySQL backend. I wrote it up using [XAMPP]("http://www.apachefriends.org/en/xampp.html"), got everything working, and now I'd like to transfer the PHP files to my Mythbuntu box, add a second database besides the mythconverg one, and use that to keep track of my books. The advantage of putting it on my Myth box is that I can log in over my network with my laptop to enter and look up my books, and then I can also log in from anywhere via the web since it's already got Apache set up for MythWeb, and it's always on.

Anyway, here's my problem. I'm unable to set up my new database on the Myth box. In installed PHPMyAdmin, and I've tried doing it through the command line, as well. I can't log in as root, it just says "ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)". I know I'm using the right password, because I *can* log in as user "mythtv". Once I'm in there, though, it says I don't have privileges to create a new database. The mythtv user works just fine otherwise, though, because I can log in and do everything through mythweb, my recordings work just fine, I've even got the flash streaming of recordings working through MythWeb.

So, help? How can I either log in as root to create the new database, or temporarily give the "mythtv" user privileges to create a new database?

---

### Post by uopjohnson on 2008-06-21
Your root and mythtv mysql passwords are probably not the same.  You might want to try mysql -u root with no password to see if you just didn't set one up otherwise you can google for mysql root password reset it is pretty easy to do.

---

### Post by Medieval Cow on 2008-06-23
That did it! I definitely had set a root password, and I thought I knew what I set it as. Thinking back though, I had set up an install of Mythbuntu to test it out, then re-installed if after I was done testing it. Since I had already set up a front-end on my laptop and didn't need to re-install that, I just copied that auto-generated mysql password over to the new install, and I guess it only changed it for the mythtv user, not root. Oops. At any rate, I was able to reset that root password, and have happily created my new database. Thanks!

---

