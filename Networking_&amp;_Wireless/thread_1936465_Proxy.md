---
title: "Proxy"
date: 2012-03-06
forum: Networking &amp; Wireless
---

### Post by bn3232 on 2012-03-06
Is there any way to use a SSL Proxy with username and password in ubuntu? I need something like proxifier which is a windows application. in gnome proxy there is no way to enter username and password for SSL proxy. So do firefox.
I use Ubuntu 11.10 with gnome 3.

---

### Post by loolooyyyy on 2012-03-23
tsocks and proxychains, tell me if works!

---

### Post by bn3232 on 2012-03-23
Thanks. proxychains also works with SSL proxies. for example:
in config file:
sudo gedit /etc/proxychains.conf
http ip port username password (the word "http" is used for a SSL proxy)
to use the proxy:
proxychains firefox (or any other app)

---

