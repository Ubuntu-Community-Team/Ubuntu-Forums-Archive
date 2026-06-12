---
title: "MythWeb Permission Denied"
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by obrient on 2007-10-04
I just updated Mythtv and all of the pluggins. I went and changed the information in the mythweb-htaccess.conf 
```

setenv db_server 
setenv db_name 
setenv db_login 
setenv db_password 
``` 

to fit my setup. I don't need to set it up with a password since it is only inside my LAN. I also made sure that the folder permissions in the /etc/var folder was set so that the directory should be accessable and can get to page inside the folder however it still isn't working. 

Is anyone having any  problems with this?? If you need more info please let me know.

---

### Post by coffeebaron on 2007-10-14
I've also got the same problem. Currently investigating.

---

### Post by coffeebaron on 2007-10-16
I found the answer in another thread.

[http://ubuntuforums.org/showthread.php?t=536555&highlight=mythweb&page=4](http://ubuntuforums.org/showthread.php?t=536555&highlight=mythweb&page=4)

The update changes the .htaccess symlink to point to /etc/mythtv/mythweb-htaccess
You need to relink it to /etc/mythtv/mythweb-htaccess.conf

---

