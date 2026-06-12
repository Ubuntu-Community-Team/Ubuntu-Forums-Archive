---
title: "There is a simple tweak to speed up mythweb!"
date: 2008-07-22
forum: Mythbuntu
---

### Post by tagra123 on 2008-07-22
I have several recording and a few hundred channels mythweb works with. Page load time were too slow for my taste so I did some googling.

Loading mythweb listing page was taking about 45 seconds now its about 12.

Found the helpful info here: [http://threebit.net/mail-archive/mythtv-users/msg11624.html](http://threebit.net/mail-archive/mythtv-users/msg11624.html)


So on my myth system I edited (yours may be different)

```
sudo gedit /etc/apache2/sites-enabled/mythwebdir
```

The original content was
```

<Directory "/var/www/mythweb">
    Options         FollowSymLinks
    AllowOverride   All
</Directory>

```

It was changed to
```

<Directory "/var/www/mythweb">
    Options         FollowSymLinks
    AllowOverride   All
    ExpiresActive On
    ExpiresByType application/x-_javascript_ "modification plus 1 year"
</Directory>

```


Try to restart apache to see if everything is correct

```
sudo /etc/init.d/apache2 reload
```

If you receive an error about no "ExpiresActive" then there are a couple more commands to install the module.

```
cd /etc/apache2/mods-available
sudo a2enmod expires
sudo a2enmod deflate
sudo a2enmod headers

```

```
sudo /etc/init.d/apache2 reload
```

The error messages about ExpiresActive should now be gone and fast page loads of mythweb.

Awesome improvement.

---

### Post by superm1 on 2008-07-22
neat fix!

Could you file a bug to make sure we add this for 8.10 by default?

---

### Post by tagra123 on 2008-07-22
Not sure it's a bug, but if you tell me where to list this I'll be glad to do it -- or you are welcome to too.

I do think most mythweb users would welcome this as default behavior.

---

### Post by tgm4883 on 2008-07-23
[https://bugs.launchpad.net/mythbuntu](https://bugs.launchpad.net/mythbuntu)

---

### Post by nickrout on 2008-07-23
it doesn't have to be a "bug" in the usual sense of being a "problem". Filing a bug puts an enhancement in a queue of things to be fixed or improved. Simple as that.

---

### Post by tagra123 on 2008-07-23
I have take your advice and filed a bug report 

It is here:  [https://bugs.launchpad.net/mythbuntu/+bug/251228](https://bugs.launchpad.net/mythbuntu/+bug/251228)

---

### Post by gndprx on 2008-07-23
Made the change and it works great.  Thanks!

---

### Post by tagra123 on 2008-07-23
> **gndprx said:**
> Made the change and it works great.  Thanks!

You are welcome. It was too good of an improvement to not share.

---

### Post by bmathis on 2008-07-24
awesome!

---

