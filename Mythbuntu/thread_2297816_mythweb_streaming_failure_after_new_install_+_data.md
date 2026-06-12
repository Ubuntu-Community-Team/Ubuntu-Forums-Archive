---
title: "mythweb streaming failure after new install + database restore"
date: 2015-10-06
forum: Mythbuntu
---

### Post by HughR on 2015-10-06
My system disk died, taking with it Ubuntu + MythTV.
I installed mythbuntu 14.04, stopped the backend, and restored the database (thank you, mythconverg!).

The result almost worked.

1) I have a lot of recordings so mythweb runs out of memory when listing them.  I have to remember to edit /etc/apache2/sites-available/mythweb.conf to change php_value memory_limit from 64M to something larger.

2) streaming from the recordings list no longer worked.  It turned out that CGI was not enabled in apache2.  How come?  For me, the fix was:
```

cd /etc/apache2/mods-enabled/
sudo ln -s ../mods-available/cgi.load
```

---

### Post by blm-ubunet on 2015-10-16
The normal way to enable/disable modules is using:
sudo a2enmod module_name or
a2dismod
but I think this does exactly same as your symlink.

Need to restart apache server:
sudo initctl restart apache2
(upstart example)

---

