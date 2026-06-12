---
title: "gnome-network-properties does not set env variable"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by bbellster on 2011-04-19
I have a problem with my proxy variables. I use gnome-network-properties gui to set up two locations. One at home with no proxy and one at work. Somehow, apt-get works fine, but wget does not. 
I checked the env variables with the following command

env | grep proxy

and get

http_proxy=http://yourproxyserver:port/
FTP_PROXY=http://yourproxyserver:port/
ftp_proxy=http://yourproxyserver:port/
all_proxy=socks://proxy.sample.com:80/
ALL_PROXY=socks://proxy.sample.com:80/
https_proxy=https://proxy.sample.com:80/
no_proxy=localhost,*.local,mirror.switch.ch,127.0.0.0/8
HTTP_PROXY=http://yourproxyserver:port/

which leads me to believe that gnome-network-properties is not setting the env variables properly.

In need help...

---

### Post by matt_symes on 2011-04-19
Hi

```
http_proxy=http://yourproxyserverport/
FTP_PROXY=http://yourproxyserverport/
ftp_proxy=http://yourproxyserverport/
all_proxy=socks://proxy.sample.com:80/
ALL_PROXY=socks://proxy.sample.com:80/
https_proxy=https://proxy.sample.com:80/
no_proxy=localhost,*.local,mirror.switch.ch,127.0. 0.0/8
HTTP_PROXY=http://yourproxyserverport/
```

Which proxy is which ?

Kind regards

---

### Post by bbellster on 2011-04-20
Well i found the problem something (bibus?) added 

http_proxy=http://yourproxyserverport/
FTP_PROXY=http://yourproxyserverport/
ftp_proxy=http://yourproxyserverport/

to my .bashrc file thereby overwriting anything gnome-network-properties put there
As to why there are so many proxy variables I have no idea

---

