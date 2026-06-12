---
title: "Ubuntu 12.04, Dell Inspiron N4030, wireless not conneccting after software update."
date: 2013-02-01
forum: Networking &amp; Wireless
---

### Post by audiobat on 2013-02-01
I am running Ubuntu 12.04 on a Dell Inspiron N4030.  I was having frustrating wireless connection problems after installing.  After searching forums for many days using my Wired connection, I found this fix, which WORKED:  
[http://forums.linuxmint.com/viewtopic.php?f=61&t=106740#p602838](http://forums.linuxmint.com/viewtopic.php?f=61&t=106740#p602838)

NOW - after the latest Ubuntu software update, I am no longer able to connect to wireless.  No error messages, it just tries to connect and asks for my password repeatedly...     Does anyone know what this last update did to undo my last fix?    I tried the same fix again but since the update my NetworkManager.conf is blank/empty/null/nada, so I cannot use the same fix.      Help Please, I am an ubuntu noob!

---

### Post by Hadaka on 2013-02-01
Hi, here ya go,build your own NetworkManager.conf

cd /etc/NetworkManager
gksudo gedit NetworkManager.conf
```
[main]
plugins=ifupdown,keyfile

dns=dnsmasq    #this is the line you commented out #
[ifupdown]
managed=false
 
```

---

### Post by audiobat on 2013-02-02
Thanks - it is up and running now.   Do you have a link to additional information so I might understand NetworkManager rather than editing code blindly...    Id' really like to learn more about networking in general, as it is the most frustrating to me.

Thanks again!

---

