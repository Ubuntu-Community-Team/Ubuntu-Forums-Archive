---
title: "No internet on desktop unable to update"
date: 2012-03-31
forum: Networking &amp; Wireless
---

### Post by ydeardorff on 2012-03-31
I have some sort of glitch in my ubuntu 11.10 desktop.
Im pulling the correct IP as far as I can tell via ifconfig but I get no internet connection.

I tried to run sudo apt-get update and got something wicked happened. The results show the http at the end of the line showing the canical address rather in front of it. yet when I check the sources.conf file it looks all like its supposed to be.

I am posting this as it isnt exactly like the other similar problems Ive found. Im not able to post my file results as I cannot get the computer in question online. It show its connected to the belkin.76a router, but will not connnect.

Yesterday I was able to get online for a short time. When the router got knocked off line, I rebooted the router and its back to not working again. restarts have no effect. 

All other computers work fine except the one desktop which is the only unbuntu system in my home.

Any help here? I cant find the problem as to why the http: show up after the canical web address, yet in the sources file its not. Is it looking in the wrong place?

---

### Post by Iowan on 2012-03-31
I presume you can ping the router. Can you ping a internet site by IP address (try 8.8.8.8)?

---

### Post by gordintoronto on 2012-03-31
What is the result of:
cat /etc/resolv.conf

Did you mean you checked sources.list? If so, how? If apt-get shows a malformed line, I'm betting there is a malformed line. Use full screen when you look at it.

I don't know what you mean by "Im pulling the correct IP."

---

