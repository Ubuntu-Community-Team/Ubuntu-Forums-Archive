---
title: "New Ampache install, http://localhost/ampache &quot;Not Found&quot;"
date: 2010-11-21
forum: Multimedia Software
---

### Post by DodgeV83 on 2010-11-21
New Ampache install, [http://localhost/ampache](http://localhost/ampache) comes up as "Not Found"

Here is the fix:

```
sudo ln -s /etc/ampache/ampache.conf /etc/apache2/conf.d/
```

Then restart apache with the following command:

```
sudo service apache2 restart
```

Seems the ampache.conf symlink isn't created there during installation.

Edit:  It seems there is already a bug for this

[https://bugs.launchpad.net/ubuntu/maverick/+source/ampache/+bug/676234](https://bugs.launchpad.net/ubuntu/maverick/+source/ampache/+bug/676234)

---

### Post by spiffbuntu on 2010-12-15
Thanks for this post. I had trouble on two ubuntu machines. Thanks =D

---

