---
title: "Apache2 Server help"
date: 2011-09-19
forum: Networking &amp; Wireless
---

### Post by inuyash274 on 2011-09-19
Alright. a few days ago i finally set up a apache2 webserver with mysql and php5. i can create and view this website by going to [http://localhost/](http://localhost/) in my browser and i can add any content i want to it. php5 was set up correctly. now. my problem is. this is all installed with basicly off line settings (as of default). how can i get it up or edit my configuration so that when people go to [http://whatevermyipaddressis/](http://whatevermyipaddressis/) they will see my website when i have my computer connected to the internet. any help?

---

### Post by Dangertux on 2011-09-19
If your server is behind a router you will either have to port forward or create a DMZ for the server, machine.

Also things to keep in mind are static versus dynamic ip's. If your ip changes frequently or really at all. You will need to use a dynamic dns provider like no-ip.com (note they also have domains fairly cheaply if you want your own .com or other top level domain).

---

