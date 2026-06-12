---
title: "Have problem in setting up LAN"
date: 2011-12-22
forum: Networking &amp; Wireless
---

### Post by askbapi on 2011-12-22
I am trying to create a LAN between a server (intel i5) and five client (intel dual core). I am using switch from d-link and a router + ADSL modem from TP-LINK. 

my LAN

INTERNET
     |
     |
MODEM + ROUTER
     |
     |
SERVER
     |
     |
SWITCH
     |- CLIENT 01
     |- CLIENT 02
     |- CLIENT 03
     |- CLIENT 04
     |- CLIENT 05
            |- printer

Server OS : Ubuntu 10.04 LST server
Client OS : Ubuntu 11.10

MY PROBLEM
I am unable to connect to LAN server . What could be the problem

---

### Post by elliotbeken on 2011-12-22
Sorry so is the server connected to the same switch ?

Do you have the correct ip addresses and have you tried to ping the devices?

---

### Post by elliotbeken on 2011-12-22
if you have the correct ip addresses and they are all connected with the correct cables then the rest of the network (router/modem) are nothing to do with it.

---

### Post by SlugSlug on 2011-12-22
snap on the avatar!

Depneds how the servr is configured, have you got DHCP installed and setup?

---

### Post by drdos2006 on 2011-12-22
Plug your server and your switch into your router and use the router to allow DHCP.

regards

---

### Post by gordintoronto on 2011-12-22
"I am unable to connect to LAN server."

Sorry, there's no information there. How about, "I did X and Y and Z and expected result A, but this other thing happened instead." Ask 10 people what they mean by "connect to" and you might get a dozen answers.

Ubuntu Server is great for high-volume web sites. For anything else, Ubuntu Desktop works just as well, and takes about 5% as much effort to set up.

---

### Post by askbapi on 2011-12-23
> **elliotbeken said:**
> Sorry so is the server connected to the same switch ?


Yes - server is connected to same switch
> 
Do you have the correct ip addresses and have you tried to ping the devices?
Yes - no response

---

### Post by askbapi on 2011-12-23
> **SlugSlug said:**
> snap on the avatar!

Depneds how the servr is configured, have you got DHCP installed and setup?

YES, DHCP installed and configure

---

### Post by askbapi on 2011-12-23
> **drdos2006 said:**
> Plug your server and your switch into your router and use the router to allow DHCP.

regards

MY router have only one Ethernet port.

---

