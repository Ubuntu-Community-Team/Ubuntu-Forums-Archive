---
title: "apache serves login page"
date: 2006-05-10
forum: Networking &amp; Wireless
---

### Post by mcioffi on 2006-05-10
Hi,

Installed apache 2 and 2 things happen that I do not know how to fix.  First,  when I browse to the server it comes up with a login page (might have the defaults set wrong somewhere, but where?).  th other fits into this also, I can only get the apache page by going to localhost/apache2-default/  So, it is not recongizing the ip 182.168.1.9/apache2-default/  or the name echo/apache2-default/   

I only had to set one conf in past versions of other distributions, but then again, my memory is shot.

thanks in advance

M.

---

### Post by matthewstory on 2006-05-10
apache2 config files:

/etc/apache2/apache2.conf  # primary config
/etc/apache2/httpd.conf       # apache 1.3 style config
/etc/apache2/ports.conf       # ports . . . yeah that one's obvious
/etc/apache2/sites-enabled/* # config for sites enabled

to add modules or pages with apache 2 instead of loading into httpd.conf or apache2.conf you merely put a virtual link to the modules in the /etc/apache2/mods-available into the /etc/apche2/mods-enabled and the same for sites-available/sites-enabled.  Hope this helps.

---

### Post by mcioffi on 2006-05-10
Hi,  Thanks for the response.  I have gone through those files (at your direction) and I am kind of getting the point.  I guess that somewhere in themis a directive enabling a login script, or maybe it is just a default when a folder is not set right.  I will keep poking around.  Thanks again,

M.

---

