---
title: "Setting autoproxy or without proxy"
date: 2013-04-24
forum: Networking &amp; Wireless
---

### Post by hbaromega on 2013-04-24
I am using Ubuntu 12.04, 64-bit.

I am using a mobile broadband data card at my home. For browsers setting autoproxy works fine.

However, when I try to use 'apt-get install' or 'apt-get update' it doesn't work.

When I work with the office LAN, by adding the following in the .bashrc

       ```
export http_proxy=http://172.16.1.1:3128
```
       ```
export ftp_proxy=http://172.16.1.1:3128
```

it works fine.

Now even if I comment these 2 lines while using mobile internet at home,* apt-get update* still looks for the same proxy! 

How can set an autoproxy like my browser?

Please help.

---

