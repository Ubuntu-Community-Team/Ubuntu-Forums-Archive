---
title: "Network service autentication"
date: 2011-09-18
forum: Networking &amp; Wireless
---

### Post by nikola.kojovic on 2011-09-18
Hello to all,
OK this i my let call it problem. I watched in one cyber cafe a type of network authentication that action can be described this way, user can easy get network access wired or wireless method is not important, but when he type any web page he get a log in page where username and password is required or any type of textual key. When he enter his credentials that are correct he can browse normally and get connectivity on other apps like IM or gaming or acces to intranet services, but when he don't enter his credentials correctly he always get that one same page that ask him for right credentials over and over again and he dont have any kind of intranet or internet access. What kind of service is that does anyone know ?

---

### Post by think13 on 2011-09-18
> **nikola.kojovic said:**
> Hello to all,
OK this i my let call it problem. I watched in one cyber cafe a type of network authentication that action can be described this way, user can easy get network access wired or wireless method is not important, but when he type any web page he get a log in page where username and password is required or any type of textual key. When he enter his credentials that are correct he can browse normally and get connectivity on other apps like IM or gaming or acces to intranet services, but when he don't enter his credentials correctly he always get that one same page that ask him for right credentials over and over again and he dont have any kind of intranet or internet access. What kind of service is that does anyone know ?

I believe that you run your own DNS server that resolves any request to the same IP address unless they enter the correct credentials. It must also be set up with some setting on the router to redirect traffic to that same address, in case the user knows the IP address he/she wants to connect to.

There are some software products that do this for you. My university had one made by Cisco, unfortunately I don't remember the name.

---

### Post by nikola.kojovic on 2011-09-18
i found something called "captive portal" i think that is i what i had in mind, but now i have problem to decide which one have multiuser support and restrictions based on authentication, anyone have any suggestion ?

---

