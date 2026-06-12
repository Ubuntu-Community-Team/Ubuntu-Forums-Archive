---
title: "Mythweb broke after upgrade to 9.04"
date: 2009-10-22
forum: Mythbuntu
---

### Post by dardack on 2009-10-22
So i finally decided to upgrade to 9.04.  Before I run a website off the same server, with mythweb directory requiring a password.

ie if you type in [www.mydoman.com](www.mydoman.com) the reg index.php came up, you would have to add /mythweb and know the userid/password to get to that part.

Now when you go to [www.mydomain.com](www.mydomain.com) it auto goes to mythweb and skips index.php, if you type in /index.php you get to that page.  How can i fix this?

I've tried adding an .htaccess to /var/www with the DirectoryIndex index.php but that didn't work.  

My /etc/apache2/httpd.conf file is blank.  Any help please.

---

