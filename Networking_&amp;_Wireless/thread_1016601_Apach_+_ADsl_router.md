---
title: "Apach + ADsl router ?"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by soulkeeperxx on 2008-12-20
Hi

i have set apacher server on my pc and i made a site add it normally and now when i go to 127.0.0.1/sitename it oppens perfectly with no problem.

the problem is i want my partner in another country to check on the progress of the site so when i go to [www.whatismyip.com](www.whatismyip.com) and copy my ip and send it to him he try to use it in the explorer but what happen is he get the user name and pass page for my adsl router instead of going to that site . its like he is going to my 192.168.1.1 instead of going to the apache ip .

how can i change that ? my adsl is assus 602g

plz help

---

### Post by bluefrog on 2008-12-20
you need to go in the admin interface of your router, disable the internet connection to your router (which is a bad idea by the way - being able to access your router interface thru the web) and then forward the port 80 to your local IP.

On second thought, the port forwarding should be sufficient on its own.

---

