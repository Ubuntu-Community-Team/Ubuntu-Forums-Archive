---
title: "Netatalk config problems 10.04.2"
date: 2011-03-19
forum: Networking &amp; Wireless
---

### Post by headz68 on 2011-03-19
Hi all,

I've been trying to create file sharing between my MacBook Pro and my Lucid Lynx box for time machine backups and media server purposes. 
I followed this guide:
 [http://sysblog.sund.org/2010/05/install-netatalk-and-avahi-on-ubuntu-10-04/](http://sysblog.sund.org/2010/05/install-netatalk-and-avahi-on-ubuntu-10-04/)

Everything seems to work with these exceptions:

[LIST=1]
[*]I can see my LucidLynx box in my finder app in my Mac but only when I run these commands from Ubuntu: ```
sudo /etc/init.d/netatalk restart
sudo restart avahi-daemon
```If I restart my LucidLynx box then I can't see anything in finder.
[*]I can't log into my LucidLynx box from finder. I don't get a bad username or password error it just tells me the connection failed. *Note if I do enter an incorrect username or password it WILL tell me it's incorrect.
[/LIST]
Any help would be appreciated. I've looked at this link below since some people have used it in theses forums but it's a bit dated and I'm not sure if it would be helpful.  
[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

---

### Post by headz68 on 2011-03-20
This guide worked for me! 
[http://blog.ibd.com/sysadmin/bonjour-avahi-netatalk-to-share-files-files-between-ubuntu-10-4-mac-os-x/](http://blog.ibd.com/sysadmin/bonjour-avahi-netatalk-to-share-files-files-between-ubuntu-10-4-mac-os-x/)


For some reason I still have to restart avahi-daemon if I restart the server. Anyone have ideas?

EDIT: I actually have to restart both netatalk and avahi in order to log in.

---

### Post by headz68 on 2011-03-20
fixed with [https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/624043/comments/17](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/624043/comments/17)

---

