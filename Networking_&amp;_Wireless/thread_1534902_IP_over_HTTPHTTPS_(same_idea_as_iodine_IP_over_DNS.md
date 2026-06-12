---
title: "IP over HTTP/HTTPS (same idea as iodine IP over DNS)"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by karit on 2010-07-20
IP over HTTP/HTTPS (same idea as iodine IP over DNS)

Hi,

I was wondering if there are any tools that allow you run IP over HTTP/HTTPS that can be password protected. Basically same idea as Iodine ([http://packages.ubuntu.com/search?keywords=iodine](http://packages.ubuntu.com/search?keywords=iodine)) does with IP over DNS. Iodine works great other than it is rather slow and looking for something over HTTP to be a little faster

Usage scenario:
There are some free WiFi hot spots that allow HTTP/HTTPS only. While I am at these hot spots I would like to be able to SSH to my server. I would like to run SSH over HTTP tunnel to my server.

* I would like it somewhat password protected so not just anyone can relay through my server
* HTTPS is in preference to HTTP
* Being a package and as easy to install and run as iodine would be good
* Being able to run as daemon is a good thing.
* Run on port 80 or 443 start as root but then drop back to a non root user for normally running like iodine can do

Thanks

---

### Post by wacky_sung on 2010-07-20
If you are using wifi and it is prone to MTM(Man in the Middle) attack especially if you are using http.Try to get wire if you wanna safe.

---

