---
title: "Sharing a file through WAN"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by status001 on 2009-05-11
I use a soft name HFS(HTTP File Server) in Windows to share my files to another user in WAN/internet. Here you can see this soft
[http://www.rejetto.com/hfs/?f=dl]("http://www.rejetto.com/hfs/?f=dl")

I want a similar soft in Ubuntu. I don't want to upload my file on any web server. And with HFS, I can also share my files/folders on LAN.

---

### Post by Peter09 on 2009-05-11
ssh is the most often used file share in Ubuntu. You need to install openssh-server and the rest is history - well nearly :)

---

### Post by dmizer on 2009-05-11
Perhaps you would be interested in this then: [http://www.rejetto.com/forum/?topic=4469](http://www.rejetto.com/forum/?topic=4469)

Alternatively, you could use any number of possibilities including ssh/scp as suggested by Peter, FTP as outlined in my signature, http via apache or lighttpd, among others.

---

### Post by status001 on 2009-05-13
I rather found the easiest way to do this. Problem is I don't know about the security issues. But it solved my problem. You have to have real IP to do this.

open terminal, change the directory which one you want to share.
write:

```
$python -m SimpleHTTPServer
``` # requires Python 2.4

or

```
$python -c "from SimpleHTTPServer import test; test()"
``` # older Python

or

```
$python -c "import SimpleHTTPServer;SimpleHTTPServer.test()"
```


**Browse on:
```
http://localhost:8000
```   #on your localhost
```
http://your.real.ip:8000/
```  #on internet

---

