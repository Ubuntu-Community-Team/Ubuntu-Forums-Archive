---
title: "how use proxy in axel download accelerator ?"
date: 2012-10-09
forum: Networking &amp; Wireless
---

### Post by snifer7 on 2012-10-09
hi every body :)
i am new to ubuntu 12.04 and i'm using "axel" download manager to download files at home .
but in university have to set proxy!
i edited this file : "axelrc" -> sudo gedit /etc/axelrc
at this file , i added "http_proxy = [http://usename](http://usename) : pass @ proxy : port/"

but when i download a file by axel , it says "authentication proxy ... "
 what shoud i do !?

should i use aria download manager?
thanks :-)

---

### Post by Parker32 on 2012-10-10
Sam Watkins wrote implemented a simple caching web proxy server using axel. It runs from inetd (He uses the package
openbsd-inetd). The script is a bit messy but it's unusual anyway to see a web proxy written in 2.5Kb of shell script.

[http://sam.nipl.net/axel-proxy/](http://sam.nipl.net/axel-proxy/)

Sam's ISP is a bit dodgy and individual TCP connections are slow while many parallel connections run fast.

It works well enough for most basic http and ftp queries, although for lots of small files it will be slower than a normal unproxied connection.

---

