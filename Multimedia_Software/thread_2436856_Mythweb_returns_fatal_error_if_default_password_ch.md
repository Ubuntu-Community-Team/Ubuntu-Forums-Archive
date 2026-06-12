---
title: "Mythweb returns fatal error if default password changed."
date: 2020-02-14
forum: Multimedia Software
---

### Post by vidtek on 2020-02-14
If mythtv is working fine but mythweb fails, then edit this file:

/etc/apache2/sites-available/mythweb.conf

There is an entry for the password and if you have changed the password in mythtv  it retains the old one
```
setenv db_server        "localhost"
	setenv db_name          "mythconverg"
	setenv db_login         "mythtv"
	setenv db_password      "*****"
```

Tony

---

