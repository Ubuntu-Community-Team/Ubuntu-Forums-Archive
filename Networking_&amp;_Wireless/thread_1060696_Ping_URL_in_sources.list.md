---
title: "Ping URL in sources.list"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by madangopalk on 2009-02-05
Hi

I was trying to ping the urls in sources.list 

ex: [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

with command: ping archive.canonical.com/ubuntu dapper-commercial main

i am only able to ping this : ping archive.canonical.com

is there any way to ping the whole address.

I am doing this because i want to check whether the link exist or not. before using it in my program.

---

### Post by steeleyuk on 2009-02-05
A ping can't tell you whether a link is available, it will only tell you that a server is connected to the network.

---

### Post by madangopalk on 2009-02-05
no but i think it is also used to know whether a website is connected. 

ie. if i use ping [www.google.com](www.google.com) i get a reply..

---

### Post by Kevbert on 2009-02-05
Just copy the address into your browser and see if a page is displayed. If it doesn't exist you'll get a http 404 error. In your example [http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/) exists (but with the /).

---

