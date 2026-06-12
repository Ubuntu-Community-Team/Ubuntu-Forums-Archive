---
title: "Proxy not working"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by bbala2020 on 2009-05-23
I've a proxy in my network to access internet (with authentication). I can use the proxy to browse internet on firefox but not able to use with wget or any os services. It says authentication required. I've set that to be the gnome's global proxy but still doesnt work. i've exported it in the terminal like export [http://username:password@host:port](http://username:password@host:port). so I'm able to ping any server but not able to wget. What could be the reason??

---

### Post by gpredrag on 2009-05-23
wget uses /etc/wgetrc or .wgetrc in users home directory. That's where you should set your proxy settings.
You can just edit and enable proxy settings in /etc/wgetrc or use it as an example for personal .wgetrc

---

