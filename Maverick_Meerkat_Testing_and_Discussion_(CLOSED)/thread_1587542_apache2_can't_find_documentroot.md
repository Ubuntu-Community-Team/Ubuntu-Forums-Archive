---
title: "apache2 can't find documentroot"
date: 2010-10-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Weaselpants on 2010-10-03
Probably not specifically a 10.10 issue, but perplexing nonetheless:
here's the deal . . .
for legacy reasons my website DocumentRoot path is /web/httpd/htdocs/
-- no matter what I change in the apache2 configuration files
(both /etc/apache2/apache2.conf and /etc/apache2/sites-available/default) the server tries to go to /etc/apache2/htdocs. My question is - where is
apache2 getting this? I have scoured my system looking for places that
this config info may be hiding but cannot find it. I need to get this
server stood up soon - anybody got any ideas here?

BTW These config files, in fact the entire /etc/apache2 directory are EXACTLY the same as on the four other servers here.  Three are Debian (2 are 5.0, 1 is 4.0) and one is Ubuntu 10.4.  They all work just fine.

---

### Post by cariboo on 2010-10-03
Documant root is set in /etc/apache2/sites-available, then a symbolic link is created by the command:

```
a2ensite mywebsite
```

Which enables the web site.

See the documentation [here]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html")

---

### Post by Weaselpants on 2010-10-04
Ran both a2dissite and a2ensite to no avail.  All they do is break/make the symlink in the /etc/apache2/sites-enabled directory.  That link is/has been there all along.  Like I mentioned - all the config files come from my other systems which are running fine.  Somehow the apache2 server thinks that DocumentRoot is /etc/apache2/htdocs - looks to me like the config files cannot override some default setting somewhere.  Hard coded maybe??  If I place a symlink in the apache2 directory pointing at the real DocumentRoot - it works.  However, like I said, that's a hack.

---

### Post by Weaselpants on 2010-10-04
Got it - it was in the virtual host configuration.  You'd think that some kind of error would show up but id didn't.  Anyways - both sites up and running now.

---

