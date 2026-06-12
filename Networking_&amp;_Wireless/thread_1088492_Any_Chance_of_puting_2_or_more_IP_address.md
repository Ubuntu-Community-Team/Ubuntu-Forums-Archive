---
title: "Any Chance of puting 2 or more IP address"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by kierangoud on 2009-03-06
Hi All,

We are using Ubuntu 8.04LTS Server and wondering whether we could add 2 or more IP address for ubuntu 8.04LTS Server.

Just i want to use it for websites. I want to call Different site with different IP Address on same machine. If possible how can i do that?

Or any other way to call sites differently with url's

Right now we got one site as default [for example: moodle site], if and trying to call another site i have to call it through default site.

Any help would be greatly appreciated!

Thanks
Kieran :0)

---

### Post by puppywhacker on 2009-03-06
1. if you want different URL's to reach the same webserver (but maybe different content) you should create a virtual host in apache.

```
http://www.site1.com
http://www.theother.org

```

2 if you want to run 2 servers, you should set one webserver to listen to another port than 80

```
http://www.me.com
http://www.me.com:8080
```

3 if you want your machine to have two ip-addresses on the same interface you have to create an alias with ifconfig
```

eth0 = 192.168.0.1
eth0:0 = 10.0.0.1
```

---

### Post by sp0nge on 2009-03-06
IMO, vurtual hosting is the way to go here. You can create multiple users and config apache to accept and use these active virtual sites. [This]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") is a good tutorial to get you up and running. 

Then, when pointing to [www.website1.com](www.website1.com), [www.website2.org](www.website2.org), or [www.mysitehere.info](www.mysitehere.info), the respective home pages will display from the same machine.

---

