---
title: "Ampache woes"
date: 2007-04-06
forum: Multimedia &amp; Video
---

### Post by TehSnarf on 2007-04-06
Using Ubuntu Edgy desktop, (fresh install, 2 days old)... not really sure if this is the place to ask but here it is anyway. Installed MySQL, Apache2, PHP5... manually installed Ampache. I can get everything into the catalog just fine, and everything seems like it _should_ work, but for some reason I'm getting a "Timed Out" error in WinAMP on WinXP machine when I try listening to the music. Not sure what all I should include where, so if you need anything, let me know.

---

### Post by cjssmo on 2007-08-27
You may need to add this to your /etc/apache2/conf.d.  Copy this and place it in a text file (your creating a apache2 virtual host)

Alias /ampache /usr/share/ampache (or where ever you have ampache installed)

<Directory /usr/share/ampache>
  Options FollowSymLinks
  AllowOverride Limit Options FileInfo
</Directory>

Ampache Forums [http://ampache.org/forums/](http://ampache.org/forums/)

IRC freenode #ampache

Hope this helps

Charlie  :)

---

