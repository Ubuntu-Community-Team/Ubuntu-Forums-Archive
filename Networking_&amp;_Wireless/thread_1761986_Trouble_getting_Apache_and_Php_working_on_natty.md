---
title: "Trouble getting Apache and Php working on natty"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by deb8torGG on 2011-05-18
Hi,

I want to try and get apache and php working on Natty.  I have got apache displaying an index page but when i try to show a php file firefox just asks me if I want to save the file and doesn't display the file in the browser.

I installed using some info from websites to install al LAMP Server which seems to have finished ok.

I have tried using php from the command line to see what happens and it seems the html is being generated ok.

Anyone got any ideas on what to check ?

Many thanks

---

### Post by kzar79 on 2011-08-02
I've had this same problem and after wasting an entire day uninstalling and reinstalling the entire server, I resolved the problem modifying */etc/apache2/mods-enabled/php5.conf*

```
    <FilesMatch "\.ph(p3?|tml)$">
        SetHandler application/x-httpd-php
    </FilesMatch>
```

-->

```
    <FilesMatch "\.ph(p*|tml)$">
        SetHandler application/x-httpd-php
    </FilesMatch>
```

I suspect that this isn't the perfect solution, and that the problem is in the installed modules and/or configured mime types.

---

