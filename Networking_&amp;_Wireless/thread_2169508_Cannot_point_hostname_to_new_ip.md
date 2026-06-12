---
title: "Cannot point hostname to new ip"
date: 2013-08-22
forum: Networking &amp; Wireless
---

### Post by lara_c2 on 2013-08-22
Hi!

I bought a new VPS and I need to move a website to that VPS. I want to test it before going live. I haven't installed nothing yet, just Apache.

Under Linux, the /etc/hosts file can be used to override dns definitions, i.e. to point an hostname to a different ip.

I added a line in the /etc/hosts file:

123.123.123.123 [www.mywebsite.com]("http://www.mywebsite.com")

- I flushed all caches and went to [www.mywebsite.com]("http://www.mywebsite.com") , but it still shows the old site.
- I used ping to test the ip and it shows the new ip.
- I used wget to retrieve the index.html file, but it retrieves the file from the old server.
- I bypassed my router to check if it's something related with it, but it isn't.
- I restarted my PC
- I checked using Linx text browser

If instead I add:

123.123.123.123 [http://ubuntuforums.org](http://ubuntuforums.org)

I still see this website. So it's not related with the new VPS

Why can't I point a hostname to a new IP? 

Is there another way to do it?

Thanks for your help!

---

### Post by zacktu on 2013-08-22
You can have a line in your /etc/hosts file such as

123.123.123.123 mywebsite

and then enter either *[http://mywebsite](http://mywebsite)* or *mywebsite* as a url in your browser.

---

### Post by lara_c2 on 2013-08-22
Thanks. I tried your suggestion, here is the output of wget:

> wget mywebsite
--2013-08-22 13:18:32--  [http://mywebsite/](http://mywebsite/)
Resolving mywebsite (mywebsite)... 192.3.90.190
Connecting to mywebsite (mywebsite)|192.3.90.190|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

I tried the usual way from another removed server:
added 
> 123.123.123.123 [www.mywebsite.com]("http://www.mywebsite.com") 
in /etc/hosts
wget [www.mywebsite.com](www.mywebsite.com) and I see the contents of the new server. So the problem is of my local connection.

---

### Post by bab1 on 2013-08-23
> **lara_c2 said:**
> ... Under Linux, the /etc/hosts file can be used to override dns definitions, i.e. to point an hostname to a different ip.

This is not quite correct.  

By **default**, _the local */etc/hosts* file is** always checked before checking with a DNS server**_.  Either your */etc/hosts *file is not correct or the* /etc/nsswitch.conf *file has been altered on this host.

---

