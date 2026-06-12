---
title: "Ubuntu on VMWare connection"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by Luna.jp on 2009-06-25
Good afternoon!

I am having an issue when trying to connect to my Apache2 webserver on Ubuntu that is running in VMware Player on my Windows XP machine. I wish to run the Ubuntu on the VM, and access the server via Windows XP but I am ran into a wall, XP won't connect.

I followed the instructions listed here to get the Apache2 server up and running and working fine in Ubuntu ([https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP))

And I can connect to the http server while in the VM, but when I minimize and come back to XP, I can't connect.

Anyone have any input on how I can achive this?
Thank you.

---

### Post by Luna.jp on 2009-06-26
Bump-a-roo!

---

### Post by KarlIvan on 2009-06-26
it might be your firewall. try turning off your firewall altogether in Ubuntu (just to isolate the problem for now) if it works after that, then your firewall would be a good place to start troubleshooting. I got an apache2 server working from Ubuntu inside of VMWare running on an XP machine, and I can access it. My firewall is completely turned off though (since I dont have it connected to the outside world), so thats my first guess

---

### Post by romeroagnelli on 2009-06-26
Try a ping to your Ubuntu Machine. If it replies, then switch off the firewall and try to access the server again.

---

### Post by Luna.jp on 2009-06-26
What you say firewall do you mean > sudo ufw disable

---

### Post by superprash2003 on 2009-06-27
first check if both machines are able to ping each other.. try accessing via ip instead of hostname

---

### Post by Luna.jp on 2009-06-27
OK, I figured it out.
In my "/etc/apache2/ports.conf" I had the following
> # Listen 80
Listen 127.0.0.1:80
Basically, I was telling the server to ONLY listen on localhost. So I removed the Listen 127.0.0.1:80 line and uncommented out the original Listen 80 line. Works now! Thank you!

---

