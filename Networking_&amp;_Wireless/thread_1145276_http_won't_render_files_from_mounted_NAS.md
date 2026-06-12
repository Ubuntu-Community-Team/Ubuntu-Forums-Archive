---
title: "http won't render files from mounted NAS"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by cbebek on 2009-05-01
Hi, I hope this is the right forum. I'm new to ubuntu so please bear with me.
 
Here goes...
 
I have lighttpd running on my main ubuntu PC and I have a NAS (DNS-323, which runs some rudimentary linux) that I mounted (with samba) into a subfolder of my web folder.
 
When using the desktop file browser, the NAS folder behaves like a native folder on my PC but when using a web browser, hrefs to some files won't work.
 
Simple HTML files on my NAS will render, PHP will render, CSS will render but some files (like GIFs and JPGs) won't render.
 
Any help would be appreciated,
Chris

---

### Post by cbebek on 2009-05-04
solved!
 

in the lighttpd.conf put

server.network-background = "writev"

on apache it's

EnableSendfile On|Off

[http://httpd.apache.org/docs/2.0/mod/core.html](http://httpd.apache.org/docs/2.0/mod/core.html)

---

